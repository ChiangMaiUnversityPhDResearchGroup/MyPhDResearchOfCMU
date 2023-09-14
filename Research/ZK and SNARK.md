# ZK and SNARK

---

title: ZKP Basic Learning Note
tags: zkp, ZKP, learning, note

author: jhfnetboy
---

## ZKP Basic Learning Note

### 概述

零知识证明最早由MIT的Shafi Goldwasser和Silvio Micali在1985年一篇名为《互动式证明系统的知识复杂性》的论文中提出。作者在论文中提到，证明者（prover）有可能在不透露具体数据的情况下让验证者（verifier）相信数据的真实性。零知识证明可以是交互式的，即证明者面对每个验证者都要证明一次数据的真实性；也可以是非交互式的，即证明者创建一份证明，任何使用这份证明的人都可以进行验证。零知识证明目前有多种实现方式，如zk-SNARKS、zk-STARKS、PLONK以及Bulletproofs。每种方式在证明大小、证明者时间以及验证时间上都有自己的优缺点。

零知识证明有三个基本特征，即：

完整性：如果statement为true，则诚实的验证者可以相信诚实的证明者确实拥有正确的信息。
可靠性：如果statement为false，则任何不诚实的证明者都无法说服诚实的验证者相信他拥有正确的信息。
零知识性：如果statement为true，则验证者除了从证明者那里得知statement为true以外，什么都不知道。
总而言之，要创建零知识证明，验证者需要让证明者执行一系列操作，而证明者只有在得知底层信息的情况下才能正确执行。如果证明者乱蒙一个结果，那么验证者极有可能在验证中发现并证明他的错误。
零知识证明的主要价值是可以在以太坊等透明的公链上利用隐私数据集。区块链本质上透明度非常高，任何在区块链网络中运行的节点都可以查看并下载所有储存在账本中的数据，而区块链结合了零知识证明技术，可以让用户和企业用隐私数据来执行智能合约，并且不透露具体的数据内容。

### 非交互式证明

零知识证明的理论基础：椭圆曲线，大数计算，群论，同态加密，配对函数

零知识证明的各种算法： zkSNARK，zkSTARK，BulletProof

**算法属性可表示为**
zk-SNARKs (简洁的非交互式零知识证明)
Zero-Knowledge
Succinct
Non-interactive
ARgument of Knowledge
关键词
见证人: 执行电路时产生的中间信号 - witness
零知识证明证明您知道一组匹配所有约束的信号（见证），而不会泄露除公共输入和输出之外的任何信号。
生成 proving_key(私有证明密钥-保密) 和 verification_key(验证密钥-可公示)
创建证明: 使用proving_key和witness(见证人),生成proof数据(证据)和可公布的数据
验证证明: 使用verification_key, proof数据和可公布的数据, 验证是否有效
目前最主流的证明协议 - Groth16
证明系统更快，并且可以实现更短的证明

**原理** – 
为什么零知识证明可以做到零交互（Non-interactive）呢？
其实原理就是利用 CRS（Common Reference String）。CRS 其实就把挑战过程中所要生成的随机数和挑战数，都预先生成好，然后基于这些随机数和挑战数生成他们对应的在证明和验证过程中所需用到的各种同态隐藏。

之后，就把这些随机数和挑战数销毁。这些随机数和挑战数 被称为 toxic waste。之所以把他们称为 toxic waste，是因为如果他们没有被销毁的话，就可以伪造证明了。

在 Zcash 项目中，大家为了安全的生成这些随机数和挑战数，使用了 MPC(multi-party computation 多方计算仪式) 技术。这样多方一起来生成 这些 toxic waste，只要不是所有人合谋，那么没有人能恢复出 toxic waste。从而保证了安全性。

到目前为止，Zcash已经创建了两组不同的公共参数。第一个仪式发生在2016年10月，就在Zcash Sprout推出之前。第二个产生于2018年，预计当年晚些时候将进行Sapling网络升级。

### 价值

ZKP提供了隐私计算的可能性舞台，隐私信用计算和贷款，DID和现实绑定又保护隐私，个人数据参与计算且保护隐私，企业数据交换计算（DeSci）等等。

Zcash等区块链已经开始采用零知识证明，用户可以**创建隐私交易，隐藏交易金额以及发送者和接收者的地址**。去中心化预言机网络可以将智能合约接入链下数据和计算资源，也可以应用**零知识证明来证明某一链下数据**，并同时在**链上隐藏数据内容**。

### d记录-d见证-d关系-d信用-d网络-d积分-d使用

这个是构建更清晰一些的社区网络的思路
一定会用到ZKP，目前初步计划身份系统基于zupass（同样是基于SNARK）的api和sdk来开发社区的一些列场景应用

#### 分层结构示意

![](https://raw.githubusercontent.com/jhfnetboy/MarkDownImg/main/img/202308242228632.png)

#### Notes

区块链与ZkSnark解决的其实是同一个问题，即Alice如何向Bob证明她拥有某物

如果Alice持续向Bob证明她的时间线上持续拥有一些轨迹，而这些轨迹的公共部分又和其他人关联绑定

则就是一个去中心化的自我身份证明，除了证明是一个Role（not only a real person，maybe a community）

**区块链的解决方案是分布式账本+共识机制，ZkSnark的解决方案则是通过密码学计算**

**区块链的实现方式是分布式的冗余系统，ZkSnark的实现方式是集中式的效率系统**

正因为这一点，区块链与ZkSnark天然具有耦合性，区块链可以将事务和状态的证明外包给ZkSnark，而自身专注于数据可用性和最终确认性，这样理论上就可以巧妙地化解区块链的不可能三角，实现区块链的指数级扩展，从而为未来10年的Web3大规模采用准备好基础设施

我想正是从这个意义上，ZkSnark可以与区块链相提并论，可以与区块链一起被看做是Web3基础设施的两根支柱

-----

```
区块链的"不可能三角"（有时也被称为"区块链三难"）是一个在区块链社区中流行的观念，表示在以下三个属性中，只有两个可以同时实现，而不是全部三个：

安全性（Security）: 这指的是网络对恶意行为的抵抗能力，如双重支付、攻击和其他安全威胁。

去中心化（Decentralization）: 它表示网络操作和验证的权力分布在多个参与者之间，而不是集中在一个中心实体手中。

可扩展性（Scalability）: 这指的是网络的能力在增加参与者和交易时保持其性能。换句话说，当网络变得越来越繁忙时，它应该能够处理更多的交易。

按照不可能三角的理念，任何区块链只能在上述三个属性中优化两个。例如，比特币和以太坊在其初始设计中优先考虑了安全性和去中心化，而牺牲了一些可扩展性。这是为什么存在许多研究和创新，如分片、第二层解决方案（如 Lightning Network 和 Plasma）等，都是为了解决区块链的可扩展性问题。

然而，这个概念仍然是有争议的。有些人认为随着技术的进步，三个目标都可以在一定程度上达到。
```

------

1. Public Guardian，只是（去中心社会关系）Reputation网络的一个应用场景：去中心证明你是你
2. 区块链+ZKP（Snark）+时间线上的多人关系证明的社区经历=去中心化Reputation
3. Zupass使我们使用的基础，Demo就做个基于开放zapass的握手积分解锁闪亮boy功能的reputation积累的活人证明，也就是2
4. 能做2，就能做更多其他，例如Pbulic Guardian（当然还有其他需要battle的）

------------

用以实现基本[逻辑运算](https://baike.baidu.com/item/逻辑运算/7224729)和复合逻辑运算的单元电路称为门电路。常用的门电路在逻辑功能上有[与门](https://baike.baidu.com/item/与门)、[或门](https://baike.baidu.com/item/或门/4962107)、[非门](https://baike.baidu.com/item/非门/1421165)、[与非门](https://baike.baidu.com/item/与非门)、[或非门](https://baike.baidu.com/item/或非门/5766427)、与或非门、[异或门](https://baike.baidu.com/item/异或门/9036416)等几种。

门电路是数字集成电路中最基本的逻辑单元。常见的门电路有TTL门电路，CMOS门电路和ECL集成电路等。

KCA--系数知识假设，全称为"Knowledge of Coefficient Assumption

CRS（COMMON REFERENCE STRING），原理如下：

- 将随机数c和t内置到 “ 系统 ” 中，即将这些参数放到链上，任何人都可以参与验证---验证者只需到链上获取参数即可，无需和证明者进行交互。

zkSNARKs--终极版

1. 系统产生内置的随机数c和t，然后产生Verifier需要发给Prover的各种参数值，这些参数值公示在链上。
2. Prover返回若干参数值。
3. Verifier验证。

关于零知识证明，有三条主要的性质：

完备性。如果证明方和验证方都是诚实的，并遵循证明过程的每一步，进行正确的计算，那么这个证明一定是成功的，验证方一定能够接受证明方。
合理性。没有人能够假冒证明方，使这个证明成功。
零知识性。证明过程执行完之后，验证方只获得了“证明方拥有这个知识”这条信息，而没有获得关于这个知识本身的任何一点信息。

在交互式零知识证明中，挑战值可以由验证者随机产生，但在非交互零知识证明中，挑战值根据Fiat-Shamir转换自动产生，Fiat-Shamir转换采用了随机预言机。一个密码学安全的Hash 函数可以近似地模拟传说中的「随机预言机」。这也是非交互证明的原理。

目前Go开发者应用零知识证明大多引用gnark库。gnark是采用Go语言开发的一个zk-SARNK的实现，目前支持Groth16（Groth16是zkSNARK的典型算法，目前在ZCash、Filecoin、Coda等项目中使用）。
https://github.com/ConsenSys/gnark

关于零知识证明的概念，最早来自于1985年，由 Goldwasser、Micali 和 Rackoff 合作发布的一篇论文 《The Knowledge Complexity of Interactive Proof Systems》 。
2010年，Groth 在它的一篇名为《Short Pairing-based Non-interactive Zero-Knowledge Arguments》的论文中提出了目前零知识证明的关键性理论，即zk-SNARK，在这个理论中，证明提供者可以向验证者以数学的方式证明信息的准确性，从而避开了需要向验证者提供的除真实性和完整性以外的其他内容。
2016年提出的Groth16算法就对证明的大小进行了精简，是目前主流的ZK算法中的基础性算法之一。
2017年提出的Bulletproof算法，设计出了一种非交互式的零知识证明，这让证明者和验证者不必在同时在线，是一种很有用的算法协议。
2018年的zk-STARKs更是提出了一种不需要可信设置的算法，这让zk-STARK的发展有了一个新的突破口。目前，很多区块链项目的零知识证明都是通过zk-STARKs算法协议来实现。



我们参考 iden3 官方最新教程文档，将指导你使用 circom2 和 snarkjs 库创建和执行你的第一个零知识证明。

Semaphore整个项目，由三部分组成：nodejs模块（客户端/服务器端以及前端页面），snark模块（zk-SNARK Groth16电路相关模块），以及以太坊上的智能合约

https://github.com/semaphore-protocol/semaphore
https://semaphore.pse.dev/

#### 信息来源

https://juejin.cn/post/7176088530454577189
https://juejin.cn/post/7205839782382321724?searchId=202309112006519E0EFC6589D4002DEF67

https://www.8btc.com/article/6807270

https://foresightnews.pro/article/detail/7104