# Security policy

GameSeek treats unauthorized access, leaked credentials, and abuse of the platform as security issues.

## Report a vulnerability

Please do not open a public GitHub issue for a security report.

Use the support form and say that the report is a security issue:

[gameseekapp.com/support](https://gameseekapp.com/support/index.html)

You can also email support@gameseekapp.com.

Include what you found, where it lives, and the smallest steps that show it. Please give the team time to fix the issue before you publish details.

Product bugs that are not security issues use the same form. See [Contributing](CONTRIBUTING.md).

## What we protect

The platform uses layered controls:

- Password hashing for account secrets
- Encryption for message content and sensitive stored fields
- TLS for traffic in transit (`https://` and `wss://`)
- Keys that are generated and stored outside the client

The design is described in [Security architecture](docs/security/architecture.md).

## Past incident

On 13 June 2026 an unauthorized request reached an administrative endpoint and returned a limited list of administrative usernames and email addresses. Password hashes, secrets, payment data, and session tokens were not in that export. The issue was closed on 14 June 2026.

The full write-up is the [incident report](docs/security/incident-2026-06-14.md).
