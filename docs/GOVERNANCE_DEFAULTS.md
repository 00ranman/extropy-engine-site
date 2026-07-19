# Governance Defaults

**Part of:** Extropy Engine v3.1
**Status:** Adopted now. Every default below is amendable by a passing governance proposal under these same rules.

## Why defaults exist

v3.0 left governance shape unresolved, which blocked implementation. v3.1 ships with concrete defaults so the system can run. The defaults are deliberately conservative and easy to revise.

## Defaults

### Quorum

- **Reputation-weighted**, **context-scoped**, **rolling window** (last 90 days of active reputation in the relevant context).
- Quorum threshold: 20% of active reputation in scope.
- Pass threshold: simple majority of votes cast at quorum.

### Proposal lifecycle

```
draft → handshake-circulation → vote → enact → audit
```

- **Draft**: any DID with non-zero reputation in the scope may submit.
- **Handshake-circulation** (7 days): proposal is broadcast; PAIs collect questions and amendments.
- **Vote** (5 days): signed votes cast and published to the DHT.
- **Enact**: if passed, parameter change takes effect at the next epoch boundary (24h).
- **Audit**: post-enactment review window (30 days) for challenge proposals.

### Scope contexts (initial set)

- `protocol` — changes to spec defaults.
- `verification` — quest-market parameters.
- `governance` — changes to the governance rules themselves (require 2x quorum and 2/3 supermajority).
- `content` — surfacing/visibility parameters.

### Emergency clause

None. There is no emergency override. If the network needs a fast change, the change still goes through the normal lifecycle; the only knob is shorter circulation/vote windows, which itself requires a `governance`-context proposal.

## Open items

See `GAPS.md` — governance gaps are tagged `[gov]`.
