## 什么是区块链

### 定义
区块链技术自身仍然在飞速发展中，目前还缺乏统一的规范和标准。

[wikipedia](https://en.wikipedia.org/wiki/Block_chain_(database) 给出的定义为：

> A blockchain[1][2][3]—originally, block chain[4][5][6]—is a distributed database that maintains a continuously-growing list of data records hardened against tampering and revision. It consists of data structure blocks—which hold exclusively data in initial blockchain implementations,[7] and both data and programs in some of the more recent implementations—with each block holding batches of individual transactions and the results of any blockchain executables.[8][better source needed] Each block contains a timestamp and information linking it to a previous block.[9]

最早区块链技术出现在比特币项目。作为比特币背后的分布式记账平台，区块链在无集中式监管的情况下，稳定运行了近八年时间，支持了海量的交易记录，并未出现严重的漏洞。

*注：比特币历史上唯一已知的漏洞事件曾导致比特币的恶意增发，但问题很快被发现并修正，相关非法交易被撤销。*

公认的最早关于区块链的描述性文献是中本聪所撰写的 [比特币：一种点对点的电子现金系统](https://bitcoin.org/bitcoin.pdf)，但该文献重点在于讨论比特币系统，实际上并没有明确提出区块链的定义和概念。在其中，区块链被描述用于进行记录比特币交易的账目。

记账技术历史悠久，[现代复式记账系统](https://zh.wikipedia.org/wiki/%E5%A4%8D%E5%BC%8F%E7%B0%BF%E8%AE%B0)（Double Entry Bookkeeping）是由意大利数学家卢卡·帕西奥利，1494 年在《Summa de arithmetica, geometrica, proportioni et proportionalità》一书中最早制定。从记账技术的角度，区块链是首个大规模的数字记账技术实现。

更广泛意义地看，区块链属于一种分布式的记录技术。参与到系统上的节点，能获取到历史记录信息；区块链数据由所有节点共同维护，每个参与维护节点都能复制获得一份完整记录的拷贝。

跟传统的数据库技术相比，其特点应该包括：

* 维护一条不断增长的链，只可能添加记录，而发生过的记录都不可篡改；
* 去中心化，或者说多中心化，无集中的控制，实现上尽量分布式；
* 可以通过密码学的机制来确保交易无法抵赖，并尽量保护用户信息和记录的隐私性。

### 基本原理
区块链的基本原理理解起来并不难。

首先假设存在一个 P2P 的数据库（这方面的技术相对成熟），剩下来就是解决如何添加数据上来。只允许添加、不允许删除避免了作伪的可能性（当然还使用一些密码学手段）。这个数据库的结构是一个链，由一个个块组成，这也是其名字的来源。新的数据要加入，必须作为一个新的块来加入。而这个块能否加入，可以通过一些手段来检验出来。

具体到比特币如何使用了区块链技术。比特币将每十分钟内所有的交易都打包在一起，这些信息组成一个块。然后，网络中所有的成员都可以试图来找到一个合法的块（比如基于当前的块的信息，加上时间、id，加上某些其它有用信息等），然后进行一些 hash 计算，并且找到的结果还得满足一定条件（比如小于某个值）。一旦算出来就可以进行全网广播，大家拿到这个算出来的结果，进行正向验证，发现确实符合条件了，就承认你算出来了。

因为算出来的概率要从数学上进行保证，比如每十分钟内大概就刚好算出来一个。所以保证了区块链每十分钟增加一个块。算出来的这个人将获取得到这个时间内所有交易产生的管理费和协议固定发放的奖励费（目前是 25 比特币）。也即俗称的挖矿。

很自然会有人问，能否进行恶意操作来破坏整个区块链系统或者获取非法利益。比如不承认别人的结果，拒绝别人的交易等。实际上，因为系统中存在大量的用户，而且用户默认都只承认他看到的最长的链。只要不超过一半（概率意义上越少肯定越难）的用户协商，最终最长的链将很大概率上是合法的链，而且随着时间这个概率会越大。


### 分类

根据参与者的不同，可以分为公开链、联盟链和私有链。

公开链，顾名思义，任何人都可以参与使用和维护，典型的如比特币区块链，信息是完全公开的。

私有链，则是集中管理者进行限制，只能得到内部少数人可以使用，信息不公开。

联盟链则介于两者之间，由若干组织一起合作维护一条区块链，该区块链的使用必须是有权限的管理，相关信息会得到保护，典型如银联组织。
