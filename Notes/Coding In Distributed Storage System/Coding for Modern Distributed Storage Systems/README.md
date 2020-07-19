# Coding For Modern Distributed Storage

## [Problem's Background(问题背景)](./Background of Distributed Storage System)

## Two Types of Erasure Codes(纠删码):

### Regenerating Codes(Time Efficient)(再生码)

Metric: Network Bandwidth

Optimize **the amount of data** communicated to repair a single last node

### Locally Repairable Codes(Space Efficient)(局部修复码)

Metric: Number of disk reads

Optimize **the number of disk** reads needed to repair a single last node

## Part One:[Local Repairable Codes](./Local Repairable Codes)

### 1.1 Locality

> 1. Locality of codeword symbols
> 2. Rate-distance-locality tradeoffs.

#### Definition

A coordinate in a linear code has **locality** **r** if it can be expressed as a linear combination of r other coordinates.



If $c_i$ is lost, it can be recovered by reading just $r$ other symbols.

Data locality $r$ : all data symbals have locality r.

All-symbol locality $r$: all symbols have locality r.



#### Locally Decodable Codes And Locally Testable Codes

#### Codes with data locality

Def: A$[n, k, d]_q$ code has data locality $r$ if each information symbol can **be expressed as a linear combination of $r$** other coordinates.

$n=k(1+\frac{1}{r})+d-2$

#### Codes with all-symbol locality

Def: An $[n, k, d]_q$ linear code has locality $r$ if each co-ordinate can be expressed as a linear combination of r other coordinates.

$ n = (k+d-2)(1+\frac{1}{r})$

**The difference between the data locality and all- symbol locality is the Codes with all-symbol locality add a local parity to every group if parity symbols of size $r$**



#### Rate-distance-locality tradeoffs

The tradeoffs between  $ n, k, d, r$

In any linear code with information locality $r$:  $$ n-k \geq [\frac{k}{r}] + d-2 \space \Rightarrow \space n \geq \frac{r+1}{r}k + d-2$$









### 1.2 Reliability

> 1. Beyond minimum distance: Maximum recoverability.
> 2. Constructions of Maximally Recoverable LRCS


