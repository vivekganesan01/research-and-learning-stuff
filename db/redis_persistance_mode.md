# Redis offers two persistence modes:

1. RDB (Redis Database Backup): Creates dataset snapshots at specified intervals. This snapshot is saved to disk and can be used to restore the data in case of a crash.
2. AOF (Append-Only File): Logs every write operation the server receives. This log is written to disk and can be replayed to reconstruct the dataset.

All for only one thing:
- Data durability


### How AOF Works

---

1. **Logging Write Operations**:
    - When a write operation (such as SET, DEL, INCR, etc.) is performed on the Redis server, the command is logged to the AOF. This log is an append-only file, meaning new entries are appended to the end of the file, ensuring that the file maintains a sequential record of all operations.
2. **Writing to Disk**:
    - The AOF is stored on disk. The frequency of writing to disk can be configured to balance between data safety and performance. Redis offers several configuration options for AOF writing:
        - **always**: Every write operation is immediately flushed to disk. This is the safest option but can be slow.
        - **everysec**: Write operations are flushed to disk every second. This is a good balance between performance and durability.
        - **no**: Writes are managed by the operating system, which decides when to flush data to disk. This can be faster but less safe.
3. **AOF Rewrite**:
    - Over time, the AOF can become large because it logs every single operation. To manage the file size, Redis periodically performs an AOF rewrite. This process creates a new, smaller AOF file that contains the current state of the database, eliminating redundant commands and consolidating the log.