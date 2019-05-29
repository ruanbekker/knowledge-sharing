## Snapshots

Q) A snapshot_weekly on 2019.05.19 made a 1TB snapshot (let's say this ran 6 hours after the daily snapshot ran with the total size of 1.1TB), will this snapshot also be an incremental one from the daily, so only snapshotted the extra 6 hours after the daily one, and then just keep the metadata of daily vs monthly

Q) And would the total storage on S3 then be 1.1TB or would daily have the size of 1TB and Monthly 1.1TB, which then consumes 2.1TB of consumed storage on S3?
