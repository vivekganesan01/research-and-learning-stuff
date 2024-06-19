# Redis offers two persistence modes:

1. RDB (Redis Database Backup): Creates dataset snapshots at specified intervals. This snapshot is saved to disk and can be used to restore the data in case of a crash.
2. AOF (Append-Only File): Logs every write operation the server receives. This log is written to disk and can be replayed to reconstruct the dataset.

All for only one thing:
- Data durability