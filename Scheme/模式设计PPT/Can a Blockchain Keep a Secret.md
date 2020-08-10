---
marp: true
theme: gaia
_class: lead
paginate: true
backgroundColor: #fff
backgroundImage: url('https://marp.app/assets/hero-background.jpg')
footer: Kaixuan Wang, UESTC
---

# 论文笔记
Can a Blockchain Keep a Secret

---
## 背景与目标
1. 以公有权益证明区块链为背景
2. 实现一个可扩展的解决方案
3. 需要将“区块链的意向”表示成一个小的区块链节点委员会
4. 在对抗移动攻击者时依然保证安全性
    - 该攻击者可以在不同时间将不同参与节点变为恶意节点
    - 但一次可污染的节点数有限制
5. 现有挑战：如果有一个委员会，那么攻击者能够将其包含节点全部变成恶意节点

---
## 解决方案
1. 采用系统的*player replacability*属性，即委员会节点被主动选出以达到区块链的共识
2. 在节点发出*single* 消息前，节点都是保持其匿名性
    - 因此攻击者无法定位这些委员会节点从而攻击这些节点。
3. 怎样在委员会节点不知道对方身份的前提下分享密钥：
    - 需要一小部分节点去恢复secret，因此恶意节点也获得了密钥。
    - cyprographic sledgehammers of witness encryption and or obfuscation
    - "committe votes to open the secret"

---
## Proactive Secret Sharing

- among members of a dynamic committee which is refreshed every few rounds.
- a handover protocol in which members of the current committee re-share the secret among the members of the next one

---
## 解决方案概述

在周期$i$, 密钥在该周期委员会成员中共享，接着委员会会改变为下一周期组成的新的委员会。委员会节点个数为$c_i$，总节点个数为$N$。

