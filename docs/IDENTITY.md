# Identity & Accountability Layer

**Part of:** Extropy Engine v3.1
**Status:** Adopted (governance-revisable)

## Purpose

Provide pseudonymous, signed, reputation-bound identity so any peer can verify a chain of action without learning the human behind it.

## Primitives

- **DID** — decentralized identifier, anchored as the genesis entry of the user's PSLL.
- **Active key** — current signing key. Rotations are themselves signed PSLL events.
- **Reputation vectors** — per-context integers (e.g. `verification`, `attestor`, `governance`, `content`).
- **Attestations** — signed claims by other DIDs about an action, scoped and timestamped.

## Properties

1. **Pseudonymous-by-default.** No real-name binding required.
2. **Selective disclosure.** A user may attach verifiable credentials (e.g. "is human", "holds X license") without revealing identity.
3. **Non-repudiable actions.** Every consequential action is signed; the signature chain leads back to the DID.
4. **Recoverable.** Social recovery and user-controlled backups; no central recovery authority.
5. **Slashing is reputation-only.** No financial penalty primitive at the identity layer.

## Threat model (summary)

- Sybil: mitigated by reputation cost of issuing/attesting, not by KYC.
- Key compromise: rotation event in PSLL invalidates prior key; peers re-anchor on the new key via the signed rotation record.
- Coercion / unmasking: the layer cannot prevent off-chain coercion; it limits damage by scoping reputation per context.

## Open items

See `GAPS.md` — identity-related gaps are tagged `[identity]`.
