# 什么是PBS

作业一般会提交到超算集群上进行计算。在集群上，一般不能随意地直接以 mpirun 运行我们的并行计算程序，而必须通过其上提供的作业管理系统来提交计算任务。集群作业管理系统可以根据用户的需求，统一管理和调度集群的软硬件资源，保证用户作业公平合理地共享集群资源，提高系统利用率和吞吐率。

PBS就是其中一种解决方案，作业通过PBS命令提交到PBS队列中，然后经由PBS分配资源运行。