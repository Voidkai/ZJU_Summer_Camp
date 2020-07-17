# Coding For Modern Distributed Storage

## Erasure Codes(纠删码):

### Regenerating Codes(Time Efficient)(再生码)

Metric: Network Bandwidth

Optimize **the amount of data** communicated to repair a single last node

### Locally Repairable Codes(Space Efficient)(局部修复码)

Metric: Number of disk reads

Optimize **the number of disk** reads needed to repair a single last node

### Locality

> 1. Locality of codeword symbols
> 2. Rate-distance-locality tradeoffs.

### Reliability

> 1. Beyond minimum distance: Maximum recoverability.
> 2. Constructions of Maximally Recoverable LRCS



## Problem And Background

System: Distributed Storage.

We should make sure that the data is **secure, reliable and integrity.**

The balance between the Code Rate ( storage efficiency) and Data Recovery

### Replication(副本策略)

Usually as the HDFS, there are two copies.

Advantage: Easily to realize and the Network bandwidth is less than other strategies.

Disadvantage: More space needed to store the data.

### Simple(简单策略)

Data: A & B

Storage: A & B & A + B & A + 2B

tolerate that less than 2 nodes are invalid. And there is extra computation and double network bandwidth which are needed to recover the data.







 





