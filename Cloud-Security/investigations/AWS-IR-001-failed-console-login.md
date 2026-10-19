# AWS-IR-001 — Failed AWS Console Login

**Status:** Investigated; intent undetermined  
**Initial severity:** Low (provisional)  
**Confidence:** Medium in the observed event details; low in any attribution or malicious-intent conclusion  
**Telemetry:** AWS CloudTrail Event History  
**Event time:** 2026-09-22 06:06:52 UTC  
**Region:** ap-south-2 (as observed during lab review)

## Executive summary

A failed AWS Console sign-in event was observed in CloudTrail. The event was recorded as a failed `ConsoleLogin`, with the error message `No username found in supplied account`. The event details indicated `MFAUsed = No`. This single event is insufficient to establish account compromise or malicious intent.

## Sanitized evidence

| Field | Observed value |
|---|---|
| Event source | `signin.amazonaws.com` (ConsoleLogin event) |
| Event name | `ConsoleLogin` |
| Result | Failure |
| Error message | `No username found in supplied account` |
| MFAUsed | `No` |
| Source IP | `[REDACTED — retain in private evidence]` |
| Account / identity identifiers | `[REDACTED]` |

The source IP and account identifiers are intentionally not reproduced in this public report. Refer to the original CloudTrail event in the AWS account for the complete record.

## Timeline

| Time (UTC) | Activity | Interpretation |
|---|---|---|
| 2026-09-22 06:06:52 | CloudTrail recorded a failed ConsoleLogin | Authentication attempt failed; no successful access is established by this event |

## Triage assessment

**Classification:** Undetermined / requires correlation. Do not label this a confirmed true positive for malicious activity based on this event alone.

**Why:** The authentication failed, and the supplied account/username was not found. This may result from a mistyped or incorrect sign-in context, but that explanation is only a hypothesis until corroborated. `MFAUsed = No` in a failed login event does not by itself demonstrate MFA bypass or successful access.

**Severity:** Low provisional severity for the isolated failure. Raise severity if correlated events show repeated failures, a subsequent successful login, suspicious API activity, an unfamiliar principal, or other evidence of account misuse.

## Follow-up investigation

1. In CloudTrail Event History, search the surrounding time window for additional `ConsoleLogin` events from the same source IP and any related identity.
2. Compare failures and successes by time, source IP, user identity, and `responseElements.ConsoleLogin`.
3. Review nearby management API events for unexpected IAM, access-key, policy, or role changes.
4. Confirm with the account owner whether the sign-in attempt was expected, using an approved channel.
5. If unauthorized access is corroborated, follow the organization's incident-response process: preserve evidence, escalate, and have an authorized administrator secure affected credentials and review active sessions.

## Detection / investigation query

CloudTrail Event History does not provide SQL-style queries; use its filters for **Event name = ConsoleLogin** and the relevant time window. For a trail delivered to CloudWatch Logs Insights, an example query is:

```sql
fields @timestamp, eventSource, eventName, sourceIPAddress,
       userIdentity.type, userIdentity.arn,
       responseElements.ConsoleLogin, errorMessage
| filter eventSource = "signin.amazonaws.com"
| filter eventName = "ConsoleLogin"
| sort @timestamp desc
| limit 100
```

Run this only against a CloudTrail log group whose event format includes these fields. Adapt the query if the logs are nested or transformed.

## Evidence limitations

- This report is based on the event details captured during the lab review, not a full export of the original event.
- The surrounding authentication sequence has not yet been correlated in this report.
- The source IP has not been attributed to a person or threat actor.
- No evidence currently establishes a successful login or account compromise.

## Closure criteria

Close as benign/expected only if context supports that conclusion and no suspicious correlated activity is found. Otherwise, keep the case open or escalate according to the evidence and organizational procedure.
