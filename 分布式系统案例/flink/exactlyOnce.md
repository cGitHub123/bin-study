exactlyOnce表示在任何情况下都能保证数据对应用的效果只有一次，不会多也不会少

流处理引擎通常为用户的应用程序提供三种数据处理语义：最多一次，至少一次和精确一次

flink实现exactlyOnce的核心在于快照机制和两阶段提交

### 快照机制

照机制能够保证作业出现fail-over后可以从最新的快照进行恢复，即分布式快照机制可以保证flink系统
内部的”精确一次“处理


### 两阶段提交

link会对接各种各样的外部系统，比如kafka，HDFS等，一旦Flink作业出现失败，作业会重新消费旧数据
，这个时候就会出现重新消费的情况，也就是重复消费，这个时候就需要两阶段提交了
