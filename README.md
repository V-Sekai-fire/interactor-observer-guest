# interactor-observer-guest

One client's check of what a zone relays: it hashes each sender's frames, tags its own for each viewer, and judges every sender from four reports.

## What is here

- `observer.sgd`: `seal` writes this client's hashes and tags into its own frames, `take` checks a frame's size, ids and tag, and `close` gives a verdict on each other sender from four reports.
- `proof/hash.sgd` and `tests/hash_proof.gd`: the proof of which hash a SafeGDScript guest can take of a frame, and what it costs.

    godot --headless --path . -s tests/hash_proof.gd [-- --control=flip]

Four parties find one that lies. The verdict codes, the tags under the pairwise keys and what the checks do not show are in `docs/wire.md` of `interactor-presence-gates`, and the gate that plants a lying zone, sender and viewer is `tests/byz_gate.gd` there.

## The other parts

Each part of the presence slice is a repository of its own in `V-Sekai-fire`, and they are checked
out side by side.

| Repository | What it holds |
| --- | --- |
| `interactor-packets-guest` | the Packet codec and the order of a body's 21 parts |
| `interactor-zone-router-guest` | the model of a zone that only routes, and the trace a relay replays |
| `interactor-observer-guest` | one client's check of what the zone relays: hashes, tags and verdicts |
| `interactor-curve-guest` | curve playback between sends |
| `interactor-replica-guest` | a shared object as four replicas |
| `interactor-anny-follow-guest` | the avatar posed from the muscle skeleton |
| `transport-zone-relay` | the relay in C, on sockets, with its load generator |
| `interactor-presence-gates` | the gates that join the parts on a real body, the videos and the ledger |

## Rules of the source

Guests are SafeGDScript and gates are GDScript run on a double-precision editor with the sandbox
built in. A gate prints a `RESULT:` line and has controls that must fail. Comments are at most 3%
of a file's lines, which `tools/comment_density.exs` of `interactor-presence-gates` checks, and
the explanation is in the documentation.

## Licence

MIT; see `LICENSE`.
