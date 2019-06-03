## Snapshots



#### Definition of an Amazon Elasticsearch Snapshot:

`>` Snapshots are backups of a cluster's data and state. State includes cluster settings, node information, index settings, and shard allocation. 


#### Elasticsearch Snapshots Tips from AWS Support

1. Snapshot includes backups of: cluster's data and state (cluster settings, node info, index settings, shard allocation)
2. Amazon ES Automated Snapshots includes just the index shards
3. Both Manual and Automated Snapshots are Incremental.
4. Snapshots cannot run concurrently. You will get an `ConcurrentSnapshotExecutionException` when another one tries to run
5. Elasticsearch must pause segment merging of the segments being snapshotted, and this consumes extra resources and overhead, Elasticsearch does not allow concurrent snapshots.
6. Manual snapshots do not support the Glacier storage class.
7. If cluster is RED as a result of RED shard/index, those indices will be skipped from manual snapshots. 
8. If you are creating a new index or archiving an existing at the time of snapshot, the snapshotting will fail. 
9. Snapshot state partial means, with in a given time, AWS ES couldn't finish taking snapshot of all the changes from the recent snapshot. 
10. In such cases, manually / programmatically make sure all the indices were snapshotted as expected. You can restore an index to see if it has all the data or not. 
