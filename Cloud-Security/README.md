# AWS Cloud SOC Investigations

Hands-on cloud security monitoring and incident investigation using AWS-native telemetry. This section documents reproducible investigations, sanitized evidence summaries, analyst decisions, and response recommendations.

## Lab objectives

- Investigate AWS management activity with CloudTrail.
- Distinguish observed facts from hypotheses and user-provided context.
- Build UTC timelines and document evidence limitations.
- Assign defensible classification, severity, and confidence.
- Practice response recommendations without creating unnecessary cloud resources.

## Investigations

| ID | Scenario | Assessment | Evidence |
|---|---|---|---|
| AWS-IR-001 | Failed AWS Console sign-in and nearby API activity | Benign / false positive based on user confirmation; low severity | [Investigation report](investigations/AWS-IR-001-failed-console-login.md); [evidence inventory](evidence/AWS-IR-001-evidence-inventory.md) |

## Reproduce the investigation

1. Open **CloudTrail → Event history** in the region where the event occurred.
2. Filter **Event name** = `ConsoleLogin` and select the relevant date/time range.
3. Inspect `eventTime`, `sourceIPAddress`, `userIdentity`, `responseElements`, `errorMessage`, and MFA-related event data.
4. Review nearby authentication and management events. Treat matching timestamps and source IPs as correlation, not proof of causation or actor identity.
5. Confirm whether the activity matches planned work with the account owner/operator.
6. Record the evidence, limitations, classification, and severity. Redact sensitive details before publishing.

## Evidence standards

- Preserve original telemetry privately; publish only sanitized evidence summaries or carefully redacted screenshots.
- Use UTC timestamps.
- Separate log-observed facts from analyst hypotheses and user-provided context.
- Never commit access keys, session tokens, account IDs, ARNs, usernames, device identifiers, or unredacted logs.
- A failed login alone does not prove compromise. Assess related activity and context before closing or escalating.
- Screenshots of CloudTrail Event History and browser activity were reviewed in the original chat, but the original image files are not available in the current task workspace. They have not been uploaded or recreated. See the [AWS-IR-001 evidence inventory](evidence/AWS-IR-001-evidence-inventory.md).

## Cost-conscious approach

Start with CloudTrail Event History and existing telemetry. Add paid services or persistent log storage only when a specific investigation objective requires them.
