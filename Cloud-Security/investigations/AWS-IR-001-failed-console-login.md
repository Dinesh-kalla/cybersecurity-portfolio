# AWS-IR-001 — Failed AWS Console Login

**Status:** Closed — benign / false positive based on user confirmation  
**Severity:** Low  
**Confidence:** Medium in the recorded event details; user-confirmed attribution, not independently established by CloudTrail  
**Telemetry:** AWS CloudTrail Event History  
**Event time:** 2026-09-22 06:06:52 UTC  
**Region:** ap-south-2 (as observed during lab review)

## Executive summary

CloudTrail recorded a failed AWS Console sign-in (`ConsoleLogin`) at the time shown above. The event's reported error was `No username found in supplied account`, and `MFAUsed = No`. The user subsequently confirmed that the activity was theirs. On that contextual basis, the case is classified as benign / false positive with low severity.

That confirmation is an analyst-provided context statement. The available event details establish a failed sign-in attempt and its recorded fields; they do not independently prove who initiated it. The failure does not establish successful access, MFA bypass, or account compromise.

## Sanitized evidence

| Field | Observed value |
|---|---|
| Event source | `signin.amazonaws.com` |
| Event name | `ConsoleLogin` |
| Result | Failure |
| Error message | `No username found in supplied account` |
| MFAUsed | `No` |
| Source IP | [REDACTED] |
| Account, principal, and identity identifiers | [REDACTED] |

Account IDs, ARNs, usernames, access key IDs, session tokens, and source details that could identify a user, device, or account are omitted from this public report. No raw CloudTrail JSON is published.

## Timeline

| Time (UTC) | Activity | Evidence / interpretation |
|---|---|---|
| 2026-09-22 06:06:52 | CloudTrail recorded a failed ConsoleLogin | The event establishes a failed authentication attempt; it does not establish successful access or actor identity. |
| During follow-up | User confirmed the activity was theirs | User confirmation supports the benign classification but is not an identity claim independently verified by the CloudTrail fields available here. |

## Assessment and disposition

**Classification:** Benign / false positive, based on user confirmation.  
**Severity:** Low.

The event failed and contains an error indicating that no username was found in the supplied account. `MFAUsed = No` on this failed event is not evidence of MFA bypass. There is no evidence in the material available for this report that establishes a successful login or account compromise. User confirmation resolves the alert context for this portfolio case, while attribution remains based on that confirmation rather than independent log proof.

## Evidence inventory and limitations

- The prior repository investigation note is the written investigation material available for this case.
- The referenced conversation contains the user's confirmation and request to update the portfolio, but exposes no screenshot or document attachments.
- No screenshots, source documents, or full CloudTrail export were available in the conversation attachments or task workspace at publication time. See [evidence inventory](../evidence/AWS-IR-001-evidence-inventory.md).
- The report therefore summarizes only the sanitized event details already recorded in the prior note. It does not claim that surrounding events were reviewed.
- The source IP and identity fields are redacted; no attribution to a person, device, or network is made from those fields.

## Investigation and response notes

The prior investigation used CloudTrail Event History to review the `ConsoleLogin` event. To reproduce or extend the review, filter Event History by **Event name = ConsoleLogin** and the relevant time range, then inspect the event time, source IP, user identity, response, error message, and additional event data. Correlate neighboring authentication and management events before drawing conclusions about access or compromise.

Example query for a CloudTrail log group in CloudWatch Logs Insights (adapt to the log schema):

```sql
fields @timestamp, eventSource, eventName, sourceIPAddress,
       userIdentity.type, userIdentity.arn,
       responseElements.ConsoleLogin, errorMessage
| filter eventSource = "signin.amazonaws.com"
| filter eventName = "ConsoleLogin"
| sort @timestamp desc
| limit 100
```

Do not include unsanitized query output in a public portfolio. If new evidence indicates unauthorized activity, preserve it privately and follow the organization's incident-response process.

## Closure

Closed as benign / false positive at low severity based on the user's confirmation that the activity was theirs. The classification records that confirmation as context; it does not state that CloudTrail independently verified the user's identity.
