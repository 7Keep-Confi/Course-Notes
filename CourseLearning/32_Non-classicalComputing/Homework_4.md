# 非经典第四次作业

## 1 请调查DNA存储近三年的现状，并阐述DNA存储的优缺点

### 1.1 DNA存储近三年现状

为了将DNA作为可用的数据存储方案，需要发展能够降低基因合成成本的DNA合成技术。DNA数据存储主要涉及**通过DNA合成进行代码编写**与**通过DNA测序进行代码阅读两个过程**。近年来，已开发出许多支持化学合成DNA的新工具和新技术，如微流体系统、电化学等，当前DNA合成主要使用基于微阵列的寡核苷酸合成技术

尽管DNA数据存储技术不断发展，但其在工程实践中依然面临诸多障碍。如在信息编码和解码过程中容易产生错误，即DNA合成和测序过程容易出错；DNA数据存储的整体写入通量应在每秒千字节左右

近年来，随着合成生物学的快速发展，以高通量DNA合成技术和人工合成染色体的技术为代表，标志着人类对 DNA 的设计合成、编辑和读取能力已经进入到一个崭新的时代。在此背景下，利用合成 DNA 进行高密度信息存储成为一个非常有前景的研究方向，得到了相关领域研究者、信息技术企业与生物科技企业的广泛关注。2020 年 11 月，微软、西部数据等 传统信息技术企业与 Twist Bioscience、Illumina等新兴生物技术公司一道，共同宣布成立了第一个 DNA 数据存储联盟，将制定全面的行业路线图，为经济高效的商业档案存储奠定基础

「DNA硬盘」的应用模式已实现了一定规模的存储验证。2018 年，华盛顿大学和微软公司的研究团队实现了 200 MB的数据存储和部分数据文件的随机访问，并于 2019 年开发了原型设备，实现了「HELLO」的自动读写，同时还设计了 DNA 保存和访问的微流控平台；2019 年，美国 Catalog 公司利用独创的 DNA 写入技术，存储了16 GB的维基百科数据，是目前最大规模的「DNA硬盘」。在国内，天津大学陈为刚等采用LDPC 码与 RS 码的乘积码保证可靠性，采用 27 万条的寡核苷酸池存储超过 3 MB数据，存储了两段有历史价值的音视频片段以及 13 000 多汉字，实现了低样本浓度、低测序覆盖度的可靠读出（图 3）。深圳华大生命科学研究院 Ping 等设计的「阴-阳」编码策略可调整均聚物长度或 GC 含量等以满足不同用户需求，实现了2.02 MB数据的存储

### 1.2 DNA存储的优缺点

#### 1.2.1 优点

DNA 用作信息存储载体，具有存储高密度、不受电磁干扰、长期高可靠和维护低成本等优势，与传统的存储介质相比，DNA存储主要具有两个优点：存储密度和稳定性。

1. 存储密度
   
   DNA信息存储密度的数量级是目前已知任何储存技术的若干倍

2. 稳定性
   
   传统的数据存储方式受限于材料本身会随着时间降解，且读取数据所需技术部分已经过时。

   DNA是一种非常稳定的分子，半衰期超过 500 年，并且，在低温条件下，DNA可以保存成千上万年。

3. 与其他数据存储介质相比，DNA含量丰富、具有可拓展性

#### 1.2.2 不足

当前 DNA 信息存储的主要挑战为**单位信息存储成本高**，**信息读写速度慢**，**无法高效对接现有信息系统**

1. 单位信息存储成本高
   
   目前，寡核苷酸池的商业合成价格大约为0.002美元/base，折合0.001美元/bit（约 $8.6×10^6$ 美元/GB），写入成本较高，是硬盘的 $10^8$ 倍

2. 信息读写速度慢
   
   DNA 信息存储的读取依赖测序技术，与磁、光、电等存储相比，读取速度较慢

3. 无法高效对接现有信息系统
   
   在物理层，造成 DNA 数据存储不可靠的因素主要包括：合成、扩增以及测序处理过程的非理想，体现在碱基的插入、缺失、替代（IDS）错误以及DNA分子或片段丢失等；在应用层，提供的用户服务需要与DNA存储特点相适配。需要注意的是，DNA 信息存储也可能给传统信息系统带来安全方面的隐患。研究者可将计算机病毒信息存储于DNA，通过DNA测序以及处理过程，访问并进入非合作方的计算机系统，造成信息安全风险

## 2 什么样的问题可以由DNA计算来求解

1. 需要进行的大量并行计算的问题。DNA计算机与电子计算机相比，最大的优势在于它的并行计算能力
2. 需要大容量储存的问题
3. 对功耗具有严格要求的问题
4. NP问题如有向 Hamilton 路、3-可着色问题、可满足性问题、连接网的可满足性问题、电路的可满足性问题等