# Local Reconstruction Codes

> The Local Reconstruction Codes(LRC) is mentioned firstly in a paper called **Erasure Coding in Windows Azure Storage**

## Introduction

LRC  **reduces  the  number  of  erasure  coding  fragments that** need to be read when reconstructing data fragments that are offline, while still **keeping the storage overhead low**. The important benefits of LRC are that it **reduces the bandwidth and I/O** required for repair reads over prior codes, while still allowing a significant reduction in storage overhead.  

The motivation of using erasure coding comes from the need to **reduce the cost of storage**. Reducing about over 50%.

### When the benefits hit comes:

1. a lost or offline data fragment
2. hot storage nodes

### The goal of the design:

1. **Reduce the minimal number of fragments** that need to be read from to reconstruct a data fragment.
2. Provide significant **reduction in storage overhead to 1.33x**

## Local Reconstruction Codes

### Definition

>  Reed-Solomon Codes: A (6, 3)Reed-Solomon code contains 6 data fragments and 3 parity fragments, and 6 fragments are always required to reconstruct a unavailable data fragments.

LRC with 6 data fragments has 4 parity fragments instead of 3 parity fragments like RS codes. And Two of the parity fragments are global parties and the other two $p_x$ and $ p_y$ are from two group of  the data fragment, $\{x_0, x_1, x_2\}$ and $\{y_0, y_1,y_2\}$

**In order to repair one data fragment, there are only3 fragments needed instead of 6 fragments in original RS code.**



### How to determine the  parameters [n, k, r] of  LRC



