# Background of Distributed Storage System

System: Distributed Storage.

We should make sure that the data is **secure, reliable and integrity.**

The balance between the Code Rate ( storage efficiency) and Data Recovery

## Replication(副本策略)

![replication_thumb](.\Pic\replication_thumb.png)

Usually as the HDFS, there are two copies.

Advantage: Easily to realize and the Network bandwidth is less than other strategies.

Disadvantage: More space needed to store the data.

## Simple(简单策略)

![simple_thumb](.\Pic\simple_thumb.png)

Data: A & B

Storage: A & B & A + B & A + 2B

tolerate that less than 2 nodes are invalid. And there is extra computation and double network bandwidth which are needed to recover the data.

## NCCloud

![nccloud_thumb](.\Pic\nccloud_thumb.png)



the advanced version of the Simple strategy and the trade-off is lower the Simple.

## Regenerating Code([Network Coding for Distributed Storage Systems](https://arxiv.org/pdf/cs/0702015.pdf))

![infocomm_thumb](.\Pic\infocomm_thumb.png)

## RAID5

![raid5](.\Pic\raid5.png)

 

A Vector: $<N, T, C, A>$  Which is used to judge the ability  and efficiency of Data Recovery.

1. N : Capacity of one node / Data scale, which represents the rate of one node's ability of storing the data.（单个节点存储容量比原始数据容量）
2. T : The most number of Nodes could be tolerated to be invalid or crashed.（最多可失效节点数）
3. C : Recovery Network bandwidth /  Capacity of one node. which represents the trade-off of the recovery of the storage.（恢复数据带宽比单个节点存储量）
4. A : How many nodes are needed to recover one node.（恢复一个节点所需总结点数）



## Reed Solomon Code[RAID6]

1. 1.5X overhead and Slower recovery
2. Need a large field : each disk is a byte-vector
3. $k$ data symbols, $n-k$ parity checks. Field size $O(n)$.
4. Any $k$ Symbols suffice for full data recovery [MDS(Maximum Distance Separable)](./MDS).

there would be high recovery cost: because we need to read $k$ other disks to recover the crash disk.



| Strategy    | Type   | rate  | <N, T, C, A>       | Description                                         |
| ----------- | ------ | ----- | ------------------ | --------------------------------------------------- |
| Replication | [3,1]  | 0.33  | <1, 2, 1, 1>       | Low efficiency of Storage                           |
| Simple      | [4,2]  | 0.5   | <1/2, 2, 2, 2>     | High rate of toleration <br>But more Data is needed |
| NCCCloud    | [8,4]  | 0.5   | <1/2,2,2 or 3/2,2> | Less C                                              |
| Infocomm    | [12,8] | 0.667 | <3/8, 1, 2, 2>     | regenerating Code                                   |
| RAID5       | [3,2]  | 0.667 | <1/2, 1, 2, 2>     | Nomal RAID                                          |

## Conclusion:

存储效率等价于编码效率，反比于检错能力。恢复带宽正比于副本的使用，反比于异或编码比率。容忍失效节点数反比于节点保存信息量，反比于编码效率和存储效率。即码率越高，在节点保存信息一定的情况下，容失效节点越少。