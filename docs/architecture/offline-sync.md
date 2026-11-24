# Offline and sync

To be written before Phase 2.

Principles already agreed:
- Every change is saved to SQLite on the device first.
- Each change has a unique id, so sending it twice does no harm.
- The app pushes its changes and pulls updates when a connection is available.
- If the server and the device disagree, the rule for who wins is decided here before coding.
