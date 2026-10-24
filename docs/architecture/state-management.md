# State Management in Delta Lake

State management in the Lakehouse provides ACID transaction guarantees, concurrency control, and time travel capabilities over raw cloud object storage.

## 1. Foundations of Lakehouse State
Unlike traditional data lakes that suffer from partial writes and dirty reads, our platform utilizes Delta Lake to guarantee:
* **Atomicity**: Writes either succeed in their entirety or leave the table unmodified.
* **Consistency**: Readers always observe a coherent snapshot without seeing in-flight modifications.
* **Isolation**: Concurrent writers are managed through Optimistic Concurrency Control (OCC).
* **Durability**: Committed transactions persist permanently in cloud storage.

## 2. The Delta Transaction Log (`_delta_log`)

All table state is recorded in an ordered sequence of JSON commit files inside the `_delta_log/` directory:

```text
_delta_log/
├── 00000000000000000000.json      # Initial commit: schema & initial parquet files
├── 00000000000000000001.json      # Append transaction: adds part-0001.parquet
├── 00000000000000000002.json      # Upsert transaction: removes old parts, adds new parts
├── ...
└── 00000000000000000010.checkpoint.parquet # Compacted checkpoint every 10 commits
```

### Commit Actions
A commit file contains discrete action entries:
* `add`: Registers a new Parquet data file with partition values and statistical metadata (min/max values, null counts).
* `remove`: Marks a previously active Parquet file as logically deleted.
* `metaData`: Updates table schema, partitioning columns, or configuration properties.
* `protocol`: Enforces reader/writer protocol version constraints.
