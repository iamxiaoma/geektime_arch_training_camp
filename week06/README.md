# geektime_arch_training_camp
极客时间架构师训练营第06周作业

#作业一（至少完成一项）：
## 1、请简述 CAP 原理。
CAP原理指的是，一致性（Consistency）、可用性（Availability）、分区耐受性（Partition tolerance）。

一致性是说，每次读取的数据都应该是最近写入的数据或者返回一个错误（Every read receives the most recent write or an error），而不是过期数据，也就是说，数据是一致 的。

可用性是说，每次请求都应该得到一个响应，而不是返回一个错误或者失去响应，不过 这个响应不需要保证数据是最近写入的（Every request receives a (non-error) response, without the guarantee that it contains the most recent write），也就是说系 统需要一直都是可以正常使用的，不会引起调用者的异常，但是并不保证响应的数据是 最新的。

分区耐受性说，即使因为网络原因，部分服务器节点之间消息丢失或者延迟了，系统依 然应该是可以操作的（The system continues to operate despite an arbitrary number of messages being dropped (or delayed) by the network between nodes）。
当网络分区失效发生的时候，我们要么取消操作，这样数据就是一致的，但是系统却不 可用；要么我们继续写入数据，但是数据的一致性就得不到保证。

对于一个分布式系统而言，网络失效一定会发生，也就是说，分区耐受性是必须要保证 的，那么在可用性和一致性上就必须二选一。

当网络分区失效，也就是网络不可用的时候，如果选择了一致性，系统就可能返回一个 错误码或者干脆超时，即系统不可用。如果选择了可用性，那么系统总是可以返回一个 数据，但是并不能保证这个数据是最新的。

所以，关于 CAP 原理，更准确的说法是，在分布式系统必须要满足分区耐受性的前提下， 可用性和一致性无法同时满足。

## 2、针对 Doris 案例，请用 UML 时序图描述 Doris 临时失效的处理过程（包括判断系统进入临时失效状态，临时失效中的读写过程，失效恢复过程）。

参考《海量分布式存储系统 Doris 的高可用架构设计分析.pdf》

# 作业二：根据当周学习情况，完成一篇学习总结
本周的课程，主要讲了分布式数据库，CAP原理，NoSQL数据库架构，ZooKeeper分布式一致性，搜索引擎基础架构等。我更加全面的了解了分布式基础架构的一些基础原理和实际的应用场景。也明白了，任何的架构都是从实际应用出发产生的，而不是凭空想象创造出来的，所有的架构方案，都应该是追求最终可落地的。