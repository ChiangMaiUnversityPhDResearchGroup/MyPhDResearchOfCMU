https://hackmd.io/@jhfnetboy/Hkrk73rka

# A quick invetigation of AA SDK
背景：要参加黑客松，基于AA做一些想法的探索，所以需要一个AA的SDK选择。

目标：从下面选择一个适合PoC，可能也适合未来的SDK

要求：可以基于SDK做我们的二次开发

 	1. SDK可信中立，不依赖特定的中心化的资源（组织、受控合约等）
 	2. 支持批量部署和批量替换（本次poc核心诉求，应该是工程层面的开发速度要求）
 	3. 钱包合约内容基于proxy可升级
 	4. proxy由可信中立控制（初期由我们自己），客户自主选择是否升级（支持不升级）
 	5. 基础流程快速搭建：创建、激活、部署、bundler搭建或者外接、paymaster指定（搭建）、social reovery搭建

----

可选范围

1. Alchemy，之前用过Alchemy的API，感觉还可以，文档和稳定性，开发上手，都还行

   1. https://github.com/alchemyplatform/aa-sdk
   2. https://docs.alchemy.com/reference/bundler-api-quickstart

2. Safe，放弃，未来可能使用（和Safe集成），因为他的AA SDK首要目标是和Safe集成

   1. ```
      The Safe{Core} AA SDK main purpose is to bring Account Abstraction to life by focusing on integrating Safe with different third parties that can be provided to developers and users to abstract the complexity that comes with setting a smart contract account.
      ```

   2. https://docs.safe.global/safe-core-aa-sdk/safe-core-sdk，https://safe.global/core

3. Official by 4337 team，未来可能备选，更底层，许多需要自己建立

   1. https://www.npmjs.com/package/@account-abstraction/sdk
   2. https://github.com/eth-infinitism/account-abstraction

4. Biconomy，据说好多人用，userop网上他们占65%

   1. https://www.biconomy.io/post/biconomy-full-stack-account-abstraction-sdk

   2. Paymaster，bundler，模块化服务，可独立使用

   3. ```
      Authorised by 'web2' tech email, social creds
      Passkey - authorised by biometrics like FaceId & Fingerprint
      Authorised by EOA
      ```

   4. 客观来说，从文档看，Biconomy更合适做快速AA相关的PoC甚至一些深度项目开发，待验证

   5. https://www.youtube.com/watch?v=qBPoVs66CxE&ab_channel=NaderDabit，一个视频

5. EtherSpot，https://twitter.com/etherspot，https://etherspot.io/

   1. 文档和产品规划看起来不错

   2. ```
      The Etherspot Prime documentation provides comprehensive guidance and resources for developers looking to integrate the SDK into their projects.
      ```

   3. https://etherspot.fyi/getting-started，几步就建立一个钱包，可以测试下

   4. 依赖web3auth，之前记得这个有些中心化的依赖服务，不太放心

   5. https://dashboard.web3auth.io/organization/Personal-research/billing

6. stack早期的一个版本：https://github.com/stackup-wallet/erc-4337-examples

   1. 可以借鉴参考结构思路，因为比较简单，构建PoC还比较费劲

7. Bnana钱包

   1. 看介绍很不错，需要深入：https://docs.bananahq.io/overview/what-is-banana-wallet

   2. ```
      Banana wallet is a pluggable SDK for applications; our vision is to provide applications with an 
      infrastructure that enables them to create a secure and seamless experience for their users.
      
      Banana wallet enables application users to create an easy-to-use, non-custodial, and secure wallet 
      inside the application. This wallet leverages ERC-4337(account abstraction) and Zero Knowledge Proofs(ZKPs).
      ```

   3. 这个看了下定位，更符合我个人一年前想做的AA SDK的样子，待验证

8. 其他：https://npm.io/search/keyword:account+abstraction

   1. bobaNetwork，这个没太了解
   2. 其他？请大家comment或者推荐


-----
个人视角难免有偏颇，欢迎大家批评指正！



