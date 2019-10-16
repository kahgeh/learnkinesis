# List streams
aws kinesis list-streams

# Write
aws kinesis put-record --stream-name kg-test --partition-key 1 --data 1

# Read
## Get iterator

$iterator = aws kinesis get-shard-iterator --stream-name kg-test --shard-iterator TRIM_HORIZON --shard-id 'shardId-000000000000' | ConvertFrom-Json

## Read

$streamData = aws kinesis get-records --shard-iterator $iterator.ShardIterator --limit 10 | ConvertFrom-Json