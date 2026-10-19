# AWS Cloud SOC Investigations

Hands-on cloud security monitoring and incident investigation using AWS-native telemetry. This section documents reproducible investigations, event evidence, queries, analyst decisions, and response recommendations.

## Lab objectives

- Investigate AWS management activity with CloudTrail.
- Distinguish observed facts from hypotheses.
- Build UTC timelines and document evidence.
- Assign defensible classification, severity, and confidence.
- Practice response recommendations without creating unnecessary cloud resources.

## Investigations

| ID | Scenario | Assessment | Evidence |
|---|---|---|---|
| AWS-IR-001 | Failed AWS Console sign-in | Benign / false positive based on user confirmation; low severity | [Investigation report](investigations/AWS-IR-001-failed-console-login.md); [evidence inventory](evidence/AWS-IR-001-evidence-inventory.md) |

## Reproduce the investigation

1. Open **CloudTrail → Event history** in the region where the event occurred.
2. Filter **Event name** = `ConsoleLogin` and the relevant date range.
3. Open the event and review `eventTime`, `sourceIPAddress`, `userIdentity`, `responseElements`, `errorMessage`, and `additionalEventData`.
4. Compare nearby authentication events for the same source and identity. Do not infer malicious intent from one failure alone.
5. Record findings in the report template and redact account IDs, usernames, and other sensitive details before publishing.

## Evidence standards

- Preserve the original event in the private AWS console; publish only a sanitized excerpt.
- Use UTC timestamps.
- Separate confirmed observations from analyst hypotheses and user-provided context.
- Never commit access keys, session tokens, account IDs, ARNs, usernames, device identifiers, or unredacted logs.
- A single failed login does not prove compromise. Escalate based on corroborating evidence and business context.
- The AWS-IR-001 conversation attachments did not include screenshots or a separate source document; the [evidence inventory](evidence/AWS-IR-001-evidence-inventory.md) records that limitation.

## Cost-conscious approach

Start with CloudTrail Event History and existing telemetry. Add paid services or persistent log storage only when a specific investigation objective requires them.
