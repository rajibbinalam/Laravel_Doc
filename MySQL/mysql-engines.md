### What is deferences among all of the MySQL storage engines

__InnoDB:__
  - ACID Compliance: InnoDB is ACID-compliant (Atomicity, Consistency, Isolation, Durability), making it suitable for transactional applications.
  - Foreign Key Support: InnoDB supports foreign keys, ensuring referential integrity.
  - Row-level Locking: InnoDB uses row-level locking for improved concurrency.
  - Crash Recovery: It has crash recovery mechanisms, ensuring data consistency after a crash.
  - Storage: InnoDB uses a clustered index and stores data in the primary key order.

__MyISAM:__
  - No ACID: MyISAM does not support full ACID compliance or transactions.
  - Table-level Locking: MyISAM uses table-level locking, which can lead to performance issues with concurrent writes.
  - No Foreign Key Support: MyISAM does not support foreign keys.
  - Full-Text Search: MyISAM is often used for full-text search capabilities.
  - Storage: Data is stored with separate files for data and indexes.

__Memory (HEAP):__
  - In-Memory: All data is stored in memory, which provides fast read and write access.
  - No Durability: Data is not persistent, and it's lost upon server restart or crash.
  - No Foreign Key Support: Memory tables do not support foreign keys.
  - Locking: Uses table-level locking.
    
__Archive:__

  - Compression: Archive storage engine is designed for data archiving and uses compression to save disk space.
  - Read-Only: It's a read-only storage engine, suitable for storing historical data.
  - No Indexes: Archive tables do not support indexes.

__CSV:__
  - CSV Format: Stores data in CSV (Comma-Separated Values) format.
  - No Indexes: CSV tables do not support indexes.
  - Read-Only: Generally used for importing and exporting data in CSV format.

__TokuDB:__

  - High Compression: TokuDB is known for its high compression rates, making it suitable for large datasets.
  - Write-Optimized: Designed for fast write operations.
  - Transaction Support: Provides ACID compliance and supports transactions.

__NDB (Cluster):__

  - Distributed Storage: NDB is a distributed storage engine designed for high availability and fault tolerance.
  - Partitioning: It supports automatic data partitioning across nodes.
  - In-Memory: Data is primarily stored in memory for low-latency access.

__FederatedX:__

  - Remote Data Access: FederatedX allows you to access tables from remote MySQL servers as if they were local tables.
  - No Local Storage: Data is not stored locally; it's retrieved from remote servers.
