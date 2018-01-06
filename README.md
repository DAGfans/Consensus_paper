# Consensus_paper
Classic papers collection for the distributed consusus 

## 分布式共识发展历史

### Lamport Clock (1978)
* 问题
  - 一致性不是简单的让两个节点最终对一个值的结果一致, 很多时候还需要对这个值的变化历史在不同节点上的观点也要一致 
  - 不能简单的以接受到消息的时间作为事件的顺序判断的依据。
  - 物理时间的不可依赖，导致事件的先后关系在分布式系统中退化为事件先后顺序的偏序关系(partital order), 问题的核心演变成如何找出因果关系来取消对物理时钟的依赖。（如果一致性继续弱化的情况下，最终一致（弱一致性）连因果关系都不需要）
* 论文：Time, Clock and Ordering of Events in a Distributed System
   * https://lamport.azurewebsites.net/pubs/pubs.html#time-clocks
* Lamport Clock
  - 是针对事件发生历史的逻辑时钟, 它让我们能够把所有的历史事件找到偏序关系, 而且不仅在各自节点的逻辑时间参考系内顺序一致, 全局上的顺序也是一致的。

![screen shot 2017-10-25 at 6 53 06 pm](https://user-images.githubusercontent.com/1134993/31995139-d625ea56-b948-11e7-9b81-468651250f7f.png)

P/Q/R是三个节点, 从下往上代表物理时间的流逝, p1, p2, q1, q2, r1, r2 …. 表示事件，波浪线表示事件的发送, 比如p1->q2表示 P把p1事件发送给了Q, Q接受此消息作为q2事件。

![screen shot 2017-10-25 at 6 54 20 pm](https://user-images.githubusercontent.com/1134993/31995186-01abe57c-b949-11e7-91c5-f3e3d159e965.png)

![screen shot 2017-10-25 at 6 51 11 pm](https://user-images.githubusercontent.com/1134993/31995072-998fbe28-b948-11e7-8d43-510a3e766b9a.png)

* 两种一致性模型（Seq，linear）
   - Sequential Consistency (1979)
     * How to Make a Multiprocessor Computer That Correctly Executes Multiprocess Programs
     * https://lamport.azurewebsites.net/pubs/pubs.html#new-approach
     * https://lamport.azurewebsites.net/pubs/pubs.html#multi
   - linearizability Consistency (1990, M.P. Herlihy & J.M Wing)
     * 线性一致性：Seq的前提下，加强进程间的操作排序

### 2PC
* 1978
* Jim Gary
* Tuxedo （XA/Open规范）
 
### 3PC
* 1981
* Dale Skeen - Nonblocking Commit Protocols
* 

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

