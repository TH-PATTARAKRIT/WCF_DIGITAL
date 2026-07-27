# Security Policy

## Reporting a security or data-exposure issue

Do not publish secrets, personal data, confidential evidence, or exploit details in a public issue.

Report suspected exposure directly to the repository owner or authorized project administrator. Include the affected path, commit, and recommended containment action without reproducing the sensitive value.

## Immediate containment

If restricted data is committed:

1. Stop further merges and releases.
2. Revoke or rotate exposed credentials immediately.
3. Remove the content from the current tree.
4. Assess reachable Git history and cached artifacts.
5. Record the incident in the controlled project register.
6. Obtain Boss approval before resuming publication.

## Repository controls

- No production evidence files
- No credentials or connection strings
- No real raw or normalized transaction data
- Mask or synthesize all examples
- Review every pull request for data leakage
