# 前言
区块链具有划时代意义及潜在的巨大影响,针对这点相信大家没有歧义，这里不多介绍。当前讨论最多的就是如何将区块链真正落地，即规模化商用。

既然要规模化商用，那么选择基础开发平台尤为关键，就和IT公司技术选型一样，我们要考虑的内容包括：
- 扩展性
- 安全性
- 运行效率
- 开发难易度
- 后期技术支持

当下很多主链（公链）百家争鸣，各自扛旗，其技术核心（共识算法）成了争论的焦点。
具有代表性的以太坊的POS，EOS的DPOS，IOTA的DAG，以及DSC，还有PBFT（古老的拜占庭将军算法），除这些之外还有VBFT、poA、PoE、poL等等吧，层出不穷。

和选择开发语言一样，没有最好，只有在特定的业务背景，特定的应用场景下选择特定的平台（共识机制），才是我们应该鼓励的做法。

# 规模化商用运行的条件
首先我们看看去中心化区块链合约（POW和POS）痛点及瓶颈：
1. 交易拥堵现象（TPS低）：
全节点记账，很多交易需要排队等待被写入区块链，为了提高优先级，还不得不支付较高的手续费。
2. 扩展性差：
BTC虽然是最大、最安全的区块链，但除了炒币交易外，很难便捷地应用于其他领域。若区块链仅限于数字货币领域，则其意义显然要大打折扣。

迫切的解决这两个最大的问题，就成了当下区块链从业者的目标。TrueChain(初链)作为创新型公有链针对交易拥堵问题，提出了“混合共识机制”，POW+PBFT相结合的方式。[[参看:TrueChain白皮书]](https://www.truechain.pro/Truechain.pdf)

取长避短，保留PBFT超级节点记账机制不动（弥补POW及POS机制下所有节点参与记账造成TPS过低的问题），将超级节点的选取权交给公链，利用POW协议作为超级节点的动态选取和协议达成，将超级节点的组建由私有链与联盟链性质转换为节点选取的公有链性质。PBFT在上，POW在下，两个账本同时运行的方式弥补单一共识机制的劣势。由此，TPS、安全性和去中心化本质得到了相对兼容。

扩展性方面，TrueChain（初链）提供产品矩阵如图:
![图1](https://note.youdao.com/favicon.ico)
- 钱包就不解释了。
- Stellar为开发者提供的合约开发平台。
- Dapp Warehouse 用户Dapp下载平台。
- TrueScan 区块链浏览器。

钱包和区块链浏览器这里就不多说了，出于商业目的考虑，几乎所有主链都有各自的钱包和浏览器。

**未来相信会有能够跨链的钱包和浏览器帮助我们统一混战的格局。**

这里重点说下Stellar 合约开发平台。它的好坏直接决定了Dapp应用是否可以简单快速的建立起来，扩展性问题是否能得到有效解决。

本来想具体安装Stellar，开发一个简单合约的，因为TrueChain客服回馈Stellar尚不能公开测试，对外开放固无法完成，大家后续期待吧。

# 尚未解决的问题
## 混合共识合约机制的问题
- 双账本记账，PBFT账本是否会比POW领先很多，导致POW的二次验证延缓？
- 特定场景下，如何建立激励手段以让POW共识机制中的节点优先记账该笔交易？
- 双账本记账会不会出现漏记?相互之间如何check？

带着以上问题，我将详细深入TrueChain的源代码研究，请关注后续更新。

作者：品德 （韩晓东）
