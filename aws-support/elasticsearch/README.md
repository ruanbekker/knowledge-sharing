## Snapshots



#### Definition of an Amazon Elasticsearch Snapshot:

`>` Snapshots are backups of a cluster's data and state. State includes cluster settings, node information, index settings, and shard allocation. 


#### Elasticsearch Snapshots Tips from AWS Support

- Snapshot includes backups of: cluster's data and state (cluster settings, node info, index settings, shard allocation)
- Amazon ES Automated Snapshots includes just the index shards
- Both Manual and Automated Snapshots are Incremental.
- Snapshots cannot run concurrently. You will get an `ConcurrentSnapshotExecutionException` when another one tries to run
- Elasticsearch must pause segment merging of the segments being snapshotted, and this consumes extra resources and overhead, Elasticsearch does not allow concurrent snapshots.
- Manual snapshots do not support the Glacier storage class.
- If cluster is RED as a result of RED shard/index, those indices will be skipped from manual snapshots. 
- If you are creating a new index or archiving an existing at the time of snapshot, the snapshotting will fail. 
- Snapshot state partial means, with in a given time, AWS ES couldn't finish taking snapshot of all the changes from the recent snapshot. 
- In such cases, manually / programmatically make sure all the indices were snapshotted as expected. You can restore an index to see if it has all the data or not. 
- Some customers make hourly snapshots to minimize the data loss (costs the same in s3 storage)
- More frequent snapshots, less performance hit on your resources


#### S3 Storage Size with Manual Snapshots

- Data size of your indicex will be the size on S3
- If total size yesterday was 1.2TB and today the total size is 1.4TB, the size on S3 will be 1.4TB
- All snapshots are incremental
