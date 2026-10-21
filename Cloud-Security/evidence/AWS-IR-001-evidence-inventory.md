# AWS-IR-001 Evidence Inventory

This folder contains sanitized portfolio material only. Raw CloudTrail JSON is intentionally excluded.

| Item | Availability | Handling |
|---|---|---|
| Investigation report | Available: [AWS-IR-001 investigation](../investigations/AWS-IR-001-failed-console-login.md) | Sanitized narrative and event timeline |
| CloudTrail event export used during review | Reviewed during the investigation; original JSON contains sensitive fields and is not published | Only the minimum sanitized fields are summarized in the report |
| CloudTrail Event History screenshot | Screenshot was shown/reviewed during the original chat, but the original image file is not available in the current task workspace | Not uploaded or recreated |
| Browser activity screenshot | Screenshot was shown/reviewed during the original chat, but the original image file is not available in the current task workspace | Not uploaded or recreated |
| User confirmation that the activity was theirs | Available in the conversation | Recorded as user-provided context, not independent log attribution |
| Separate source document / notes file | No separate attachment is available in the current task workspace | Investigation notes are preserved in the report |
| Raw CloudTrail JSON | Not published | Do not commit raw events, session credentials, access key IDs, account IDs, or other sensitive fields |

## Publication checklist for later screenshots

Before uploading any original screenshots, review and redact account IDs, ARNs, usernames, source IPs where appropriate, access key IDs, session tokens, request/event identifiers, browser profile details, and other personal or account-identifying information. Do not fabricate replacement screenshots or claim a screenshot is original if it was recreated.
