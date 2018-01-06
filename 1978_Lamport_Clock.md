The concept of one event happening before another in a distributed system is examined, and is shown to define a partial ordering of the events. A distributed algorithm is given for synchronizing a system of logical clocks which can be used to totally order the events. The use of the total ordering is illustrated with a method for solving synchronization problems. The algorithm is then specialized for synchronizing physical clocks, and a bound is derived on how far out of synchrony the clocks can become.

通过定义事件的偏序关系来检查分布式系统的事件发生的先后。即通过一种分布式算法来同步系统的逻辑时钟，来给事件进行全局排序。


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
