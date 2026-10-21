# AWS-IR-001 — Sanitized Evidence Summary

This summary records the evidence discussed during the hands-on investigation. It is not a raw log export and is not a substitute for the original CloudTrail record.

## Event observations

- **2026-09-22 06:06:52 UTC — ConsoleLogin:** Failure. Error message: `No username found in supplied account`. `MFAUsed = No` on this failed event.
- **2026-09-22 06:07:31 UTC — Root identity session context:** A root-identity session was recorded; session context indicated MFA authenticated.
- **2026-09-22 06:07:35 UTC — DescribeRegions:** Read-only API call from the same source IP associated with the failed login.
- **User confirmation:** The user stated the related activity was theirs.

## Analyst interpretation

The events are close in time and share a source IP, so they are worth reviewing together. Those facts do not prove that the failed login caused the root session or independently identify the actor. User confirmation provides the benign context for closing this portfolio exercise.

**Disposition:** Benign / false positive based on user confirmation.  
**Severity:** Low.

## Evidence handling

Source IP, account identifiers, ARNs, usernames, access key IDs, session tokens, event IDs, and request IDs are omitted. The original screenshots were reviewed in the chat but their image files are not available in the current task workspace, so no screenshot is included here. The original CloudTrail export is not published.
