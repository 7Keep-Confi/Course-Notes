# 大数据复习

## 第七章 MapReduce

### 7.1 一些概念

#### 7.1.1 MapReduce模型简介

MapReduce将复杂的、运行于大规模集群上的并行计算过程高度地抽象到了两个函数：**Map** 和 **Reduce**

在MapReduce中，一个存储在分布式文件系统上的大规模数据集，会被切分成许多 **独立** 的小的数据块(这样独立的小数据块又称作 **分片spilt** )，这些分片可以被多个Map任务并行处理

MapReduce的设计理念是「计算向数据靠拢」，而不是「数据向计算靠拢」，这样可以减少因为数据移动产生的网络传输开销。

本着这样的理念，MapReduce框架会尽可能将Map程序 **就近** 安排在HDFS数据所在的节点运行，也就是 **将计算节点与存储节点放在一块运行** ，从而减少了节点间数据移动的开销

#### 7.1.2 Map 和 Reduce 函数

MapReduce 模型的核心是 Map 函数和 Reduce 函数

Map 函数和 Reduce 函数都是以<key,value>作为输入，按一定的映射规则转换成另一个或一批 <key,value> 进行输出

![Map和Reduce](images/2023-02-04-12-51-49.png)

* Map函数的输入来源于分布式文件系统中的文件块，这些文件块的格式是任意的，可以是文档、二进制格式等待
* Map函数会将输入的元素转化成 <key, value> 形式的键值对。需要注意的是，这里的key不具有唯一性，可以生成相同key的多个键值对
* Reduce函数的作用就是将输入的一系列具有相同键的键值对以某种方式组合起来，输出处理后的键值对，结果会合并成一个文件

例如上图给出的例子，Map函数的输入是一个键值对，其中key表示行号，value表示行号对应的一行文本，经过Map函数处理后，会输出一系列键值对，其中key表示出现的字符，value表示出现的次数(都为1)，这些键值对是计算的中间结果

随后，经过一些操作后，将上述中间结果转化成 <k, List(v)> 的格式，这里的value值可以理解成一个列表，key仍然是出现的字符，value是该字符出现次数组成的列表，经过Reduce处理后，也就是把相同字符出现的次数都相加，最后输出键值对，表示字符以及对应的总次数

### 7.2 体系结构

MapReduce体系结构主要由四个部分组成，分别是：Client、JobTracker、TaskTracker以及Task

![MapReduce的体系结构](images/2023-02-04-13-04-54.png)

1. Client
   * 用户编写的MapReduce程序通过 Client 提交到 JobTracker 端
   * 用户可以借助 Client 提供的接口查看作业运行状态

2. JobTracker
   * JobTracker负责资源监控和作业调度
   * JobTracker监控所有的 TaskTracker 和 Job 的健康状况，一旦发现故障，就将相应的任务转移到其他的节点
   * JobTracker跟踪任务的执行进度与资源使用量等信息，并将这些信息告诉 TaskScheduler(任务调度器) ，该调度器会在资源空闲时，分配合适的任务去使用空闲资源 

3. TaskTracker
   * TaskTracker接收JobTracker发送过来的命令并执行相应的操作如启动新任务、杀死任务等
   * TaskTracker会周期性地通过「心跳」将本节点上 **资源的使用情况** 和 **任务的运行进度** 等汇报给JobTracker
   * TaskTracker使用「slot」等量划分本节点上的资源量(CPU、内存等)
  > 一个 Task 只有获得了一个「slot」才有机会运行，调度器的作用就是将各个TaskTracker上空闲的「slot」分配给相应的 Task使用。
  > slot 还分为 Map slot 和 Reduce slot，以供Map Task 和 Reduce Task 使用

4. Task
   * Task分为 Map Task 和 Reduce Task 两种，均由 TaskTracker 启动

### 7.3 工作流程

### 7.4 具体执行阶段

### 7.5 Shuffle过程

### 7.6 WordCount实例
