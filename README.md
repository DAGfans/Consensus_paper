> **Copyright Notice**
> 
> All papers here are collected from the public domain. The copy-right owned by the original authors or orgniazation. listed here only for convenience of the personal study and not for profit or commercial.
> 
> Strictly speaking, some of papers might not allow to republish or post on servers. If true, the paper will be removed from the collection immediately and replaced by the link to the original place where the paper has been downloaded.

# Consensus_paper
Classic papers collection for the distributed consusus 

## 分布式共识发展历史

### Lamport Clock (1978)
* 论文：Time, Clock and Ordering of Events in a Distributed System
   * https://lamport.azurewebsites.net/pubs/pubs.html#time-clocks
* Lamport Clock
  - 是针对事件发生历史的逻辑时钟, 它让我们能够把所有的历史事件找到偏序关系, 而且不仅在各自节点的逻辑时间参考系内顺序一致, 全局上的顺序也是一致的。
  
### 2PC
* 1978
* Jim Gary
* Tuxedo （XA/Open规范）
 
### 3PC
* 1981
* Dale Skeen - Nonblocking Commit Protocols

### 拜占庭将军问题
* 1982
* Lamport - The Byzantine Generals Problem
* https://en.wikipedia.org/wiki/Byzantine_Generals_problem

### FLP不可能原理
* 1985
* FLP是论文作者（Fischer, Lynch and Patterson）名的缩写。
* No completely asynchronous consensus protocol can tolerate even a single unannounced process death. [ Impossibility of Distributed Consensus with One Faulty Process,Journal of the Association for Computing Machinery, Vol. 32, No. 2, April 1985] **在异步网络环境中只要有一个故障节点, 不存在一个共识算法能解决一致性问题。**
* 在允许节点失效的情况下，纯粹异步系统无法确保一致性在有限的时间内完成。
* **同步**：网络中节点间的时钟误差存在上限，消息传递必须在一定时间内完成，否则为失败；同时节点完成处理消息的时间是一定的。
   * 对于同步系统，可以很容易判断消息是否丢失
* **异步**：网络中节点时钟差异可以很大，消息传输时间可以任意长，节点处理消息的时间也可以任意长。
   * 那么消息无法响应无法知道是传输故障还是节点故障。
* 工程上通过付出代价的方式来达到共识。
   - DSCD中提到的三种解决办法

### CAP原理
* 2000
* 一致性consistency、可用性availability、分区容忍性partition **无法同时保证**
* **一致性** ：这里之强一致性，任何操作都是原子的，发生在后面的事件能够看到前面事件发生所导致的结果。（换句话，即保证结果一致，也保证过程／顺序一致）
  - 弱化一致性 ： Gossip，CouchDB，Cassandra
* **可用性** ：在有限时间内，任何非失败节点都能应答请求。
  - 弱化可用性 ：MongoDB、Redis、MapReduce。Paxos、Raft。
* **分区容忍** ： 允许网络分区（脑裂），即节点直接通信无法保障。
  - 弱化分区容忍 ：2PC，Zookeeper

### Paxos
* 1990 ～ 2001
* Paxos Made Simple (2001) 

### Zookeeper

### Raft

### PBFT

### POW (bitcoin)
* The Bitcoin Backbone Protocol: Analysis and Applications
  - https://eprint.iacr.org/2014/765.pdf
  - http://crypto.2014.rump.cr.yp.to/59182e301d011c3b5b6146b8cdf91815.pdf

### POS

