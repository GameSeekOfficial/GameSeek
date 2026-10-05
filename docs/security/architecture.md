# Security architecture

GameSeek uses separate layers for accounts, message content, stored data, and the network. Each layer covers a different failure.

## 1. Authentication

- Passwords are stored as hashes, not as the original password.
- Memory-hard algorithms are preferred.
- Older algorithms may remain only where an existing account still needs them.

The goal is that a stolen database does not hand over usable passwords.

## 2. Messages

- Message content is encrypted before it is stored or sent on.
- Only the people allowed to read a message can decrypt it.
- This encryption is separate from HTTPS. Transport security is an extra layer, not the only one.

The goal is that message contents stay confidential even if the server is compromised.

## 3. Data at rest

- Sensitive database fields are encrypted on write.
- Decryption happens when the application actually needs the value.

The goal is to limit damage from a database leak.

## 4. Transport

- Clients use HTTPS and WSS.
- Certificates identify the server.

The goal is to stop a network attacker from reading or altering traffic in transit.

## Keys

- Keys are not hardcoded in source.
- They are generated in a controlled place and kept in a narrow scope.
- Keys that protect server data are not sent to clients.
- Rotation is supported where the design allows it.

## What this is meant to resist

- Access without an account or without the right role
- Offline password guessing
- Network interception
- Message tampering
- A copied database
- A stolen session

## Path of a message

```text
User message
    → encryption
    → secure storage
    → protected database
    → TLS
    → delivery
```

## Limits

Cryptography only helps when the primitives and the key handling are implemented correctly. The design still needs updates and review. No layer replaces operational care: patching, access control, and monitoring.

## See also

- [Security policy](../../SECURITY.md) for how to report an issue
- [Incident report, 14 June 2026](incident-2026-06-14.md) for a resolved administrative-access incident
- [About](../about.md) for what personal data may be logged
