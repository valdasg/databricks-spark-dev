In Apache Spark, a core is a basic computational unit of CPU in Spark cluster. When we speak about a core in Spark, it's not about the physical cores in the CPU, but a logical representation that can execute a task in parallel. It's also often referred to as a thread.

On the other hand, a slot is a concept closely related to the core. A slot is essentially a place holder for task execution. Spark has two types of slots: CPU slots and GPU slots, for tasks that need to be executed on CPU or GPU respectively.

1. **Spark Core**: In Spark, each task runs on one core, which means that one core can process one task at a time. In other words, if a machine has multiple cores, it can run multiple tasks concurrently. Hence, the number of cores can greatly impact the parallelism of your Spark job. If a node in your Spark cluster has 8 cores, it can potentially run 8 tasks at the same time.

2. **Spark Slots**: Each core has a slot, so if a node has 8 cores, it also has 8 slots. When a task is scheduled to be run by the Spark scheduler, it is assigned to an available slot. If all slots are occupied, the task will have to wait until a slot is freed up. The number of slots in a Spark application is the maximum number of tasks that can run in parallel.

Spark has some configuration parameters related to this, like `spark.task.cpus`, which is used to specify the number of cores to allocate for each task, or `spark.executor.cores`, which is used to specify the number of cores to be used on each executor.


AQE properties:
```python
spark.sql.adaptive.coalescePartitions.enabled

spark.sql.adaptive.autoBroadcastJoinThreshold

spark.sql.adaptive.maxShuffleHashJoinLocalMapThreshold

spark.sql.adaptive.skewJoin.enabled

spark.sql.adaptive.skewJoin.skewdJoinPartitionFactor

spark.sql.adaptive.skewJoin.skewedPartitionThresholdInBytes
```