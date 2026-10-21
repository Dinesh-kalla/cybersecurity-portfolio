# AWS-IR-001 — Failed AWS Console Login

**Status:** Closed — benign / false positive based on user confirmation  
**Severity:** Low  
**Confidence:** High in the recorded event fields; attribution is based on user confirmation, not independently established by CloudTrail  
**Telemetry:** AWS CloudTrail Event History  
**Primary event time:** 2026-09-22 06:06:52 UTC  
**Region:** ap-south-2 (as observed during lab review)

## Executive summary

CloudTrail recorded a failed AWS Console sign-in (`ConsoleLogin`) at the time shown above. The event reported `No username found in supplied account`, with `ConsoleLogin = Failure` and `MFAUsed = No`. During follow-up, the user confirmed the related project activity was theirs. The case is therefore closed as benign / false positive at low severity.

The investigation also reviewed nearby CloudTrail activity. A root-identity session was recorded at 06:07:31 UTC, followed by a `DescribeRegions` event at 06:07:35 UTC from the same source IP as the failed login. The root session's context showed MFA authenticated. These are temporal and source-IP correlations, not proof that the failed login caused the root session or that the same person generated both events. The user's confirmation supplies the benign context for this lab disposition.

## Sanitized evidence

| Time (UTC) | Event | Observed result / interpretation |
|---|---|---|
| 2026-09-22 06:06:52 | `ConsoleLogin` | Failure; error: `No username found in supplied account`; `MFAUsed = No` |
| 2026-09-22 06:07:31 | Root-identity session context | Session creation recorded; MFA context marked authenticated |
| 2026-09-22 06:07:35 | `DescribeRegions` | Read-only API activity from the same source IP as the failed login |
| During follow-up | User confirmation | User stated the related activity was theirs |

Source IP, account ID, principal identifiers, usernames, ARNs, access key IDs, session tokens, request IDs, and event IDs are omitted or redacted in this public report. No raw CloudTrail JSON is published.

## Assessment and disposition

**Classification:** Benign / false positive based on user confirmation.  
**Severity:** Low.

The failed sign-in is a real recorded authentication failure, but it does not itself establish successful access, MFA bypass, or compromise. The nearby root-session and API events were correlated by time and source IP; those fields alone cannot establish causal linkage or actor identity. The user confirmed the related project activity was theirs, providing the context used to close this exercise.

## Investigation steps

1. In AWS CloudTrail, open **Event history** in the relevant region and filter by `ConsoleLogin` and the relevant time range.
2. Inspect `eventTime`, `eventName`, `userIdentity`, `sourceIPAddress`, `responseElements`, `errorMessage`, and MFA-related event data.
3. Review nearby authentication and management events. Treat same-IP and close-timestamp matches as correlation, not proof of causation.
4. Ask the account owner/operator to confirm whether the activity matches planned lab work.
5. Record the classification, severity, evidence limitations, and any remaining follow-up actions.

## Screenshots and source material

Screenshots of the CloudTrail Event History and browser activity were reviewed during the original chat investigation. The original image files are not available in the current task workspace, so they have not been uploaded to this repository. The evidence inventory records this limitation. No screenshot has been recreated or presented as original evidence.

The raw CloudTrail export is intentionally excluded because it contains sensitive account and session fields. If the screenshots are uploaded later, redact account IDs, ARNs, usernames, source IPs where appropriate, access key IDs, session tokens, event/request identifiers, and other identifying details before publication.

## Example CloudWatch Logs Insights query

For a CloudTrail log group with compatible field extraction, adapt this query to the actual schema:

```sql
fields @timestamp, eventSource, eventName, sourceIPAddress,
       userIdentity.type, userIdentity.arn,
       responseElements.ConsoleLogin, errorMessage
| filter eventSource = "signin.amazonaws.com"
| filter eventName = "ConsoleLogin"
| sort @timestamp desc
| limit 100
```

Do not publish unsanitized query output. The query is a reproduction aid, not evidence that CloudWatch Logs was used in this investigation.

## Closure

Closed as benign / false positive at low severity based on the user's confirmation that the related activity was theirs. CloudTrail established the recorded event fields and nearby API activity; it did not independently verify the user's identity or prove causation between the failed login and the subsequent root-session activity.
