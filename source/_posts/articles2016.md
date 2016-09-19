---
title: 2016精选文章推荐(9月6日-9月12日)
date: 2016-08-09T14:01:43.000Z
subtitle: 9月6日-9月12日
layout: post
author: kris.zhang
header-img: head.jpg
wechat_pig: wechat.jpg
mathjax: true
tags:
  - 精选文章推荐
---

> 越来越需要过滤的本质是因为信息爆炸，而过滤的本质应该是一种分类。越精细，就越准确，效果也就越好，个性化也就越强，也这能够解释为什么推荐系统越来越流行。

![head](articles2016/wechat.jpg)

# 9月13日-9月19日

[单点系统架构的可用性与性能优化](http://mp.weixin.qq.com/s?__biz=MjM5ODYxMDA5OQ==&mid=2651959480&idx=1&sn=337bd74410a6bef616128fd17abd08a8&scene=21#wechat_redirect) [lvs为何不能完全替代DNS轮询](http://mp.weixin.qq.com/s?__biz=MjM5ODYxMDA5OQ==&mid=2651959595&idx=1&sn=5f0633afd24c547b895f29f6538baa99&scene=1&srcid=0918OyETJpC1RcycQYlZLYTk#rd)

> 这两篇文章有些类似，第一篇主要讲解了单点系统如何保证可用性，主要有shadow-master模式、减少与单点交互、水平扩展等。我看这个问题的本质其实就是一种分散技术，将单点分散，至于怎么分散，实际上就是技术选型上的事情。第二篇文章讲解了接入层架构技术演进，包括DNS、nginx+keepalive lvs+keepalive DNS轮询等技术。

[JVM源码分析之堆外内存完全解读](http://mp.weixin.qq.com/s?__biz=MzIzNjI1ODc2OA==&mid=403168235&idx=1&sn=ecc804ba7231996d43c05138566d074a&scene=19#wechat_redirect) [JVM源码分析之不可控的堆外内存](http://mp.weixin.qq.com/s?__biz=MzIzNjI1ODc2OA==&mid=2650886854&idx=1&sn=ae73716af7b7a778955117e85e3e85db&chksm=f32f6679c458ef6f09282b9c5eb1bc571abe0d2effd384980ad24153f9e9ed0ae273038a10a9&scene=0#rd)

> 这两篇文章主要分析了对外内存的实现原理，使用场景，以及作者遇到的一个堆外内存的问题。这个人是支付宝的寒泉子，jvm团队的，在内网中经常看到他的文章，然后觉得写的很不错，这里我推荐一下，有问题可以直接粘贴给他，他还是比较热心解决各种千奇百怪的问题。

[水平分库分表的关键步骤以及可能遇到的问题](http://mp.weixin.qq.com/s?__biz=MzA5Nzc4OTA1Mw==&mid=2659598156&idx=1&sn=b5d4e509dc6a9c908bef2bad8ce27a25&scene=0#rd)

> 这篇是分库分表的一个概览。里面又很多内容我在工作中真的用到了，比如id分配，我们的这边id分配规则要比雪花算法更复杂一些。在领域建模的时候最重要的就是分片规则和策略，这些我们可以同使用中间件来自定义（写groovy脚本或者实现java接口）然后中间件根据规则自动帮你路由到指定数据源。我们规定是需要尽量避免跨分片，真的需要跨分片，中间件只能帮你做有限的事情，性能也很差，因此类似count计数这种，我们都是配合tair缓存。

[黄东旭：分布式数据库模式与反模式](http://mp.weixin.qq.com/s?__biz=MzI3NDIxNTQyOQ==&mid=2247484004&idx=1&sn=36d30d0446f7ca16eb9ca7dced100ffc&scene=1&srcid=0912IZoRcFJHqL37SFAv2Tvx#rd)

[MySQL 和 B 树的那些事](http://blog.jobbole.com/105644/)

> 关于mysql和B+树的文章非常多，这篇是我见过写的最清楚的文章了。适合入门了解使用，实际上若不是做底层架构，这种结构平常代码中基本上用不到。

# 9月6日-9月12日

[深度长文：我对CQRS/EventSourcing架构的思考](http://mp.weixin.qq.com/s?__biz=MzA5Nzc4OTA1Mw==&mid=2659598125&idx=1&sn=ca39d804aede5ee46988b6d635217027&scene=0#rd)

> 我看这篇文章的感受是，作者对cqrs和es架构的介绍非常清晰(Event Sourcing)，解释的也相当准确，易懂和到位，让我真的了解了这种读写分离式的架构概念和优缺点，是一篇不可多得的深度好文，不过文章关于架构实施方面讨论比较少，也没有成熟的系统应用案例介绍，有点纸上谈兵之嫌疑。这似乎是由于框架本身并没有支持到位。期待后续作者能够亲自在生产环境中应用这种架构

[分布式事务：不过是在一致性、吞吐量和复杂度之间，做一个选择](http://mp.weixin.qq.com/s?__biz=MzA5Nzc4OTA1Mw==&mid=2659598134&idx=1&sn=f5f73354d162a7561b3d73c204a4d1f5&scene=0#rd)

> 分布式事务是分布式系统中永恒的主题，文章题目起的挺吊炸天的，实际上是分布式事务实现方案的简介和对比，包括：2pc/3pc，Sagas长事务、事务补偿、可靠事件、TCC。实际上我们公司自己的事务框架采用的就是TCC方式。不过牛逼的在于他能够支持事务的嵌到，这点在长链路应用中是很方便的。文章可以作为一个分布式事务解决方案概览。其中sagas在上篇文章也有提到。可以了解一下，技术到不难，但是实现挺复杂。

[10亿级微博消息系统的架构演进](http://mp.weixin.qq.com/s?__biz=MzI4NzE1NTYyMg==&mid=2651101741&idx=1&sn=7fce36c155d0cb2f165098bf48be362c&chksm=f021cee4c75647f2e98b2da322cd98c12649afe202f9ade72f906007266b0733cf346f371072&scene=1&srcid=0910RnQQaH5t8TldJObgL3aW#rd)

> 这个系统说白了就是一个类似微信的chat系统，不过从功能角度讲相对简单一些。由于跟我目前从事的工作有一定关系，因此这里单独分享出来。我们关于chat的实现也比较类似，不过比微博支持更多的额外功能，比如国际化等。作者的讲解也是采用演进的方式进行，其中应对峰值和双端版本一致性问题的处理还是蛮有意思，值得学习的。不过就修改redis代码来讲，个人觉得还是应该慎重采用。

[JDK8对并发的新支持](http://mp.weixin.qq.com/s?__biz=MjM5NzMyMjAwMA==&mid=2651477476&idx=2&sn=a1dedde454b576a965c152d90ad44028&scene=1&srcid=0910MAZRErJs0P131ZJYL4dV#rd)

> 文章很简单，就说了jdk8中的几个针对并发的改进，一共有三块，一个是LongAdder，这个之前Doug lea在guava中就已经有了。还有一个是CompletableFuture，这个是为了配合stream api搞出来的，本身提供了很多方便的特性；还有一个是StampedLock用于提供一种新的读写锁活化机制，避免读多写少的场景下，写饿死。

[单日峰值2T发送量邮件营销平台实践经验](http://mp.weixin.qq.com/s?__biz=MzIwODA4NjMwNA==&mid=2652897991&idx=1&sn=c26ebf0782817e44b6a2892c6ae04033&chksm=8cdcd688bbab5f9ebbea47157bdb727fed83be344f2aa0e1236e46e05ba70f99a7343777cba6&scene=0#rd)

> 本文是京东EDM平台的架构演变和优化方案的概述。所谓EDM，Email DirectMarketing 的缩写，即邮件营销。其实说白了就是一个邮件服务中心。业务调用API接口发送邮件。系统将EDM分为两个部分，一个是生产品台，一个是发送平台。中间通过一个redis优先级队列进行任务分派。我觉得这个设计还是蛮赞的，不过采用redis的优先级队列我倒是觉得虽然轻量，但是对于后期多样化的任务分发方式可能会让代码不便（当然我不太了解业务）。除此之外，文章的一些优化思路是值得学习的，毕竟作者就是做着方面出身的。

[分层编译对逃逸分析的影响](http://mp.weixin.qq.com/s?__biz=MzAxMjQ5NDM1Mg==&mid=2651024173&idx=1&sn=8e616311d7876a74b9088799f884cb28&scene=1&srcid=0906v2y8FfaDmEAdiVP2RBi2#rd)

> 朝晖大神的文章还是可以读一读的，这篇文章讲了两个主要概念，一个是分层编译，一个是逃逸分析。逃逸分析是一个种分析手段，他所带来的好处诸如标量替换、锁消除，栈上分配。标量替换，可以理解为将对象打散，栈上分配可以减少GC压力，锁消除能够消除局部锁比如StringBuilder。深入jvm虚拟机那本书也都讲过，不过真正能弄明白还需要去做一些简单的对比试验。文章这方面做得非常棒！

# 8月30日-9月5日

[JVM的Stop The World，安全点，黑暗的地底世界](http://calvin1978.blogcn.com/articles/safepoint.html?hmsr=toutiao.io&utm_medium=toutiao.io&utm_source=toutiao.io)

> 白衣江南的博客有两个特点，其一是文笔比较幽默，其二是文末总要来一个'美女福利'。这篇文章讲解java的safepoint概念，给了几个jvm的常用参数，用来观察安全点触发时间和操作类型。简单来说安全点就是JVM STW时的一个时间点，这个点以后所有线程停止执行，从而vm线程执行某些操作，但这里不一定GC，比如instrumentation，取消偏向锁等等。文章的外链引用也值得仔细一读，jvm的知识点很多，需要平时一点一滴的慢慢积累。

[MySQL 中你应该使用什么数据类型表示时间？](http://mp.weixin.qq.com/s?__biz=MjM5NjQ4MjYwMQ==&mid=2664608099&idx=1&sn=0ad26c4963d68d8b00a553b43143afde&scene=1&srcid=0903ZqOzLqSQvoMbbWy5ewOn#rd)

> mysql关于时间，你是应该用INT还是timestamp还是datetime，有人说我喜欢用timestamp，为什么呢？他好，但是相比datetime有什么优势呢？作者的最后结论是在mysql中最好使用datetime，为什么？详见 本文吧！

[在产品运营中，为什么我们需要打造爆款？](http://mp.weixin.qq.com/s?__biz=MjM5OTEwNjI2MA==&mid=2651732211&idx=1&sn=2f3cbe81ab5b223667fe21135a924bfd&scene=0#rd)

> 人人都是产品经理的这个公共号真心不错，非常多的干货，我觉得作为一个程序员，也需要锻炼自己的产品思维，因此我打算尽量挑一些这上面的好文章分享。本篇文章教你如何打造爆款产品。大家熟知的一个逻辑陷阱：如果平台没有用户，商家是不会来你这里的；如果平台没有商家，用户是不会来你这里的。如何解决这个逻辑陷阱呢？其实打造爆款就是一个好的解决思路。

[可视化与领域驱动设计](http://mp.weixin.qq.com/s?__biz=MzI3MzEzMDI1OQ==&mid=2651814846&idx=1&sn=9348fd89557cf90d042353c8c47ed21d&scene=1&srcid=0904VrIlR0Yz3aP0gYYk9MSo#rd)

> 本文主要探讨了如何获得Bounded Context，如果你没有听过Bounded Context，那么你需要看一下关于DDD的内容了，或者看一下《微服务设计》。总之你进行系统设计一定需要清晰明确的定义你的边界上下文，就像细胞膜一样。这篇文章从一个可视化角度教你如何获得这个界定上下文。颠覆了我对画图的认知。原来还可以在白板上折腾出这么有用的东西！

[开源离线数据同步工具 DataX 升级至 3.0，支持十余款主流开源数据系统](http://mp.weixin.qq.com/s?__biz=MjM5NjQ4MjYwMQ==&mid=2664608092&idx=1&sn=83c3d9c9b6a7ea36a9f3fc1c462daf03&scene=1&srcid=0903JyIFlMoof9Edw5RwkYNP#rd)

> DataX 是阿里巴巴集团内被广泛使用的离线数据同步工具/平台，实现包括 MySQL、Oracle、HDFS、Hive、OceanBase、HBase、OTS、ODPS 等各种异构数据源之间高效的数据同步功能。这篇文章基本上参考了datax的官方文档，他讲解了datax的设计理念和实现方式。通过这篇文章能够大概了解datax所能做到的事情。如果你听说过阿里巴巴的canal，这个有点类似，不过datax支持的数据库更多一些，也更灵活。蚂蚁内部似乎也是用datax做数据同步。

# 8月23日-8月29日

[深入理解JDBC的超时设置](http://www.importnew.com/2466.html)

> 这篇文章从一个线上故障入手，分析了transcation超时、statement超时，socket超时的意义和实现原理，以及遇到的问题。其中操作系统层面也有一个默认的socket超时时间。不过这里并没有给出比较好的设置建议，个人觉得第一次配置的时候我们需要经验设定，然后通过历史数据进行求解

[Pitcher无线接入系统](http://mp.weixin.qq.com/s?__biz=MzA3NDcyMTQyNQ==&mid=2649255537&idx=1&sn=f5747b82de62640fc3142950dd13a813&scene=1&srcid=0823piIHCMqzDu2n3h9WRf1L#rd)

> 这个是一篇非常不错的文章，使用go实现了一个反向代理中间件，具有非常好的性能和灵活性，通过这篇文章能够了解到反向代理服务器的一些设计要点，比如进程模型，热配置加载等等，文章还提到了module模型也是值得深入学习的。

[浅谈高可用的系统](http://mp.weixin.qq.com/s?__biz=MzIyNjE4NjI2Nw==&mid=2652557200&idx=1&sn=57777ca94f596cf2864bdb60d8cb1ba7&scene=1&srcid=0823UYmq2xZDiHb8rltmNNyM#rd)

> 这个是一篇老文章了，读了很多遍，一个公共号又推荐出来了。也有很多人没有读过，因此mark到这里。作者主要谈对高可用架构的理解，从多方面进行思考，最后升华到公司对待工程的科学精神。我读该篇最大收获就是理解了高可用并不只是代码写的可靠，而是一整套的流程，管理，质量控制，测试，等等多方面

[一篇文章说透当下大热的一元夺宝！](http://mp.weixin.qq.com/s?__biz=MjM5OTEwNjI2MA==&mid=2651732124&idx=2&sn=db0eb23b9e757164e67b882e85a7e378&scene=1&srcid=0823uJnJW6JkYqgBhA3nwxX4#rd)

> 这不是一篇技术文章，但是写的非常好，分析了目前整个一元购得市场情况和风靡原因。记得一元购业务刚 刚兴起的时候，网易一元购的童鞋想拉我入伙，我看了一下，觉得市场擦边球过于走险，于是回绝了。

[高性能数据库连接池的内幕](http://mp.weixin.qq.com/s?__biz=MzI3MzEzMDI1OQ==&mid=2651814835&idx=1&sn=cb775d3926ce39d12fa420a292c1f83d&scene=0#rd)

> 之前加过这哥们的微信，然后有一天偶然在朋友圈中看到一个特别好的朋友点赞，然后我才知道，这哥们跟我的好朋友是室友。互联网圈子真是小啊。文章我有仔细读过，caelus名字不明白什么意思。其中讲了很多优化技巧值得学习，比如inline、链接复用、事务优化，无锁对象池等。如果了解pg的话，pg里面有一个中间件叫做pg-bouncer这个是一款数据库连接池，用来解决分布式系统节点过多，造成单机数据库活动链接被占满。他的思路是bouncer集群与数据库建立稳定的链接数目，其他节点通过短连接与bouncer进行交互，这样能够极大提高链接数量。按照这个思路，我们是不是可以采用中间件技术，分库分表规则路由放到中间件上，然后线程池就可以正常使用dbcp等，把节点做强，并且是可横向扩展的。这个中间件可以使用go等高并发编程友好的语言编写。客户端值需要与这个中间件代理打交道就可以了，也可以使用短连接。

# 8月15日-8月22日

[SRE：源自Google的DevOps最佳实践 | 学在GOPS](https://mp.weixin.qq.com/s?__biz=MzA4Nzg5Nzc5OA==&mid=2651661472&idx=1&sn=0a829928448dfeb6a562225a709b3bf7&scene=1&srcid=0817JtU5CDpqdLQLVxOU3RTh&key=8dcebf9e179c9f3a9e324b5e9bb376658ba9844434e14b7c46cb666af3225673a269a9985ee91e491b63fe395ec31997)

> 来自谷歌的分享，能让你全面了解到谷歌的devops的日常，读完以后感觉特别不觉明历，也羡慕谷歌工程师能够接触到全世界最好的资源和最大的流量实践

[Qunar App 用户个性化需求预测](https://mp.weixin.qq.com/s?__biz=MzA3NDcyMTQyNQ==&mid=2649255448&idx=1&sn=f6a40d64672aec55032e54fe999ee05e&scene=1&srcid=08215d4xFo3X9GK3pQ0JkY6g&key=8dcebf9e179c9f3a58f2817148510331a174a183c29dc165bfbf8784a1ed0d6735297d50dde6f857fbbb84a39be0b26e)

> 这篇文章讲的不够详细，具体的算法细节可能要自己看了，不过他大概给了一个猜你喜欢的实现思路，带有时间序列的item based CF有点意思。然后通过主观贝叶斯，rankboost lambdamart做合并排序。值得去学习下具体的算法实现。

[如何实现1080P延迟低于500ms的实时超清直播传输技术](https://mp.weixin.qq.com/s?__biz=MzAwMDU1MTE1OQ==&mid=2653547697&idx=1&sn=acc748b7fcf0058b58e244970e51eabc&scene=1&srcid=0820reEzHqOlZ448ghwmt7uR&key=8dcebf9e179c9f3a987e2a3d648565893815cd8c1540ab1c530f173748c924f73e9d971599867dbf631a9e2854a96570)

> 纯干货，围绕着视频传输的整个链条进行梳理，讲解了各个可能影响视频传输延迟的每个点，然后着重从协议层解决延迟问题，他们公司基于udp设计实现了一套视频传输协议，重点讲解的就是这个协议，作者经验还是非常丰富的。

[运维小技巧：使用ss命令代替 netstat](https://mp.weixin.qq.com/s?__biz=MjM5MTY2Mjg3Ng==&mid=203157012&idx=2&sn=1f632c067a75764a071d02bf6175cfd2&scene=1&srcid=08170W444hdKhetpY2M4zvH2&key=8dcebf9e179c9f3a210b4739f460023f56db492f2b27fb7aa7a7a50bbaae5f773066d7a64da11f69929444ed3501d5fc)

> 如果你还是在使用ifconfig，那么你应该更新你的工具库了，使用iproutes代替nettools吧！ss真的要比ifconfig快很多。

[是时候闭环Java应用了](https://mp.weixin.qq.com/s?__biz=MzIwODA4NjMwNA==&mid=2652897928&idx=1&sn=5087d67b74478deb38904fd1ec2283e3&scene=1&srcid=0816KoLf266CbGobn6s1IOzh&key=8dcebf9e179c9f3a8352cb27ba15c9a984a6547095b4c2aa2c462219c535aaa90c1691f2f284344ab3615067c6868970)

闭环你的应用，这个原则很实用在微服务场景下，qunar的配置都在写在服务器的启动脚本的，系统环境实际上我们只需要一个jre即可，使用什么容器都应该是使用者去定义

[关于自动化配置还有什么好说的呢？](https://mp.weixin.qq.com/s?__biz=MjM5NzM0MjcyMQ==&mid=2650067203&idx=1&sn=2a6eaef84d7151a119192c9294252e11&scene=1&srcid=0816842T49q6mNGwhpFct8T6&key=8dcebf9e179c9f3ad2b9c679657617fe0a8c256a2c21c3dad522d246c848752e0825214387ea3f246886c2d4859638db)

> 这个对于配置的本质思考的不错，我们应该将其理解成一个系统状态，而不是一堆脚本，值得思考一下

[基于Event Sourcing和DSL的积分规则引擎设计实现案例](https://mp.weixin.qq.com/s?__biz=MzA5Nzc4OTA1Mw==&mid=2659597948&idx=1&sn=754df1597fd042537be8c25d073d3c98&scene=1&srcid=0815xhG0D7IBlMhPFs7n3opv&key=8dcebf9e179c9f3afca03c779c05f96af61b4fd17bd119f51c5cdeb101dd815e0ada562b942c141ba0130b65853a6105)

> 积分是一个常见的场景，他可以单独抽象出一个公共服务。作者设计的这套积分系统所用到的技术并不复杂，事件总线，规则引擎DSL，都是值得学习的。但是有一点有一些不太同意，就是插件那块，有可能后期插件的维护成本变得很高。动态规则这里也可以更深入的挖掘一下，目前规则看似比较单一。有空研究一下规则引擎。

# 8月9日-8月14日

- [今日头条User Profile系统架构实践](https://mp.weixin.qq.com/s?__biz=MzIwMjE5MDU4OA==&mid=2653120041&idx=1&sn=8c23e7e57a6d67ca950bd03416e10bcd&scene=1&srcid=0811TZpMXz0murN4vMB9SKhY&key=305bc10ec50ec19b8305b459684e251fff70c870a7e446cd20ac06625ff20e01bd4849112e9635346a9c3e0ea32a4c72&ascene=0)
- [一次完整的HTTP事务是怎样一个过程？](https://mp.weixin.qq.com/s?__biz=MzIyMDA1MzgyNw==&mid=2651968318&idx=1&sn=afdf34f979bfa70d28026ae09a37af6e&scene=1&srcid=0812FDmzqdsGDUQRI2dgTIPo&key=305bc10ec50ec19b0062327810e9da251783c71797d6e4ac830ae47ed3eb66d5e5a9188a80d557e03a4f6c36c328f4a9&ascene=0)
- [Netty精粹之TCP粘包拆包问题](http://my.oschina.net/andylucc/blog/625315)
- [从Redis+Lua到Goroutine，日均10亿次的股票行情计算实践](https://mp.weixin.qq.com/s?__biz=MzA5Nzc4OTA1Mw==&mid=2659597912&idx=1&sn=14483afd4edc8489088dd58e578006a3&scene=1&srcid=0809cxUUY5gPJtHH4JC6kIj3&key=305bc10ec50ec19bccca3de586e28e0c2099428ecaaa8892a989837d033dfb4ca1e76b12b792a9918a10617063c251ec&ascene=0)
- [深入浅出 Redis Cluster 原理，来自一次干货分享](https://mp.weixin.qq.com/s?__biz=MzA3MzYwNjQ3NA==&mid=2651296996&idx=2&sn=5f4811d73e74e2a63b1cb0d3d532862a&scene=1&srcid=0809bE4ldt4f9zFdEe9vBnEi&key=305bc10ec50ec19b404b95cdce31ea34f6e82cc223dfa678dc71e07b578cf9d3904451dc3f2e1164269e583537ced87b&ascene=0)
- [美团大数据平台架构实践](https://mp.weixin.qq.com/s?__biz=MzA5NzkxMzg1Nw==&mid=2653160359&idx=1&sn=ebf8b4f3ec2a9bd76fbbf42cc29365e6&scene=1&srcid=0814pItCuni5MtX2swkhWhOO&key=305bc10ec50ec19b2ae3da6e8beef6c4733c682246acb308f4ef12a4a7bef43f6995a8608f1aced7c1a87f06765a6275&ascene=0)
- [蘑菇街电商交易平台服务架构及改造优化历程](https://mp.weixin.qq.com/s?__biz=MzAwMDU1MTE1OQ==&mid=2653547663&idx=1&sn=4de30a5a792d9442ef6015b554182913&scene=0&key=305bc10ec50ec19b4d8ec7c2400b10a8492e0abeb82139bf7dafa5c2dd4a73a7cc66e2690a14ff0be829b092e01b4842&ascene=0)
- [聊聊容器网络那些事儿](https://mp.weixin.qq.com/s?__biz=MzA5OTAyNzQ2OA==&mid=2649691135&idx=1&sn=bb0b74bdc5d0904eb23772d83a5f09a5&scene=1&srcid=0814mTlTY6K5fMXUGyCpq2SU&key=305bc10ec50ec19b15604bab6c4b0e408ded506ee15ac473d3b92c400a6d97dfccb1f7a7b7f2693d36b78bab15c473a1&ascene=0)
- [分布式开放消息系统(RocketMQ)的原理与实践](http://www.jianshu.com/p/453c6e7ff81c)
- [百姓网 Elasticsearch 2.x 升级之路](https://mp.weixin.qq.com/s?__biz=MzAwMDU1MTE1OQ==&mid=2653547666&idx=1&sn=f57978358640a8af61d6cbf404ef32b9&scene=1&srcid=0814seAbhqfetGeSh4zXbs2Q&key=305bc10ec50ec19bb4a37dbd8cfb1d18b1054200cc9b15dca6ad5097b37f98f689c048241f6f6b9343e00e02f156d77c&ascene=0)
- [Elasticsearch 架构以及源码概览](https://mp.weixin.qq.com/s?__biz=MzIyNjE4NjI2Nw==&mid=2652557005&idx=1&sn=d92465682845c4f07254f6ce28b72abf&scene=0&key=305bc10ec50ec19bd4b4dafcb7d198ee8d8094674eb215f3b497cd9d59f1c5e1dc39c44ff8338d9125ba9db7b9d82665&ascene=0)
- [Linux 中 fcntl()、lockf、flock 的区别](http://blog.jobbole.com/104331/)
- [Java的LockSupport.park()实现分析](http://blog.csdn.net/hengyunabc/article/details/28126139)
- [Redis压缩列表原理与应用分析](http://my.oschina.net/andylucc/blog/715325)
- [Java中的纤程库 - Quasar](http://colobu.com/2016/07/14/Java-Fiber-Quasar/)
- [京东评价系统海量数据存储设计](https://mp.weixin.qq.com/s?__biz=MzIwODA4NjMwNA==&mid=2652897895&idx=1&sn=ca450cf86a75af53101edf7bf0d691e8&scene=0&key=305bc10ec50ec19b344e9ce74c973c390fd739d8b08ce318b375bc2b3ee2d23ba7531d5fb29374eb4eb50144e73bdacd&ascene=0)

# 8月1日-8月8日

- [豆瓣对服务化改造实践的若干思考][1]
- [途牛订单的服务化演进][2]
- [Mercury:唯品会全链路应用监控系统解决方案详解(含PPT)][3]
- [Netty的http client连接池设计][4]
- [Google的QUIC协议：从TCP到UDP][5]
- [从Netty到EPollSelectorImpl学习Java NIO][6]
- [OS 造成的长时间非典型 JVM GC 停顿：深度分析和解决][7]
- [Java NIO之EPollSelectorImpl详解][8]
- [一个由多线程而引发内存溢出故障的案例分析][9]
- [美团外卖系统架构演进与稳定性的探索][10]

# 其他

- [性能优化模式-美团技术][111]
- [CAP理论十二年回顾："规则"变了][112]
- [分布式系统的事务处理-酷壳][1112]
- [序列化和反序列化-美团技术][114]
- [大规模SOA系统中的分布事务处事_程立][115]
- [Cache应用中的服务过载案例研究][116]
- [软件架构模式-gitbook][117]
- [开源软件架构-中文版][118]
- [Apache Cassandra架构理解][119]
- [一篇文章掌握所有开源数据库现状][1110]
- [CoreOS 实战：剖析 etcd(这篇文章讲解raft很好)][1111]
- [分布式系统的事务处理][1112]
- [微信序列号生成器架构设计及演变][1113]
- [Redis和Memcached的区别][1114]
- [各种推荐系统相关的介绍][1115]
- [面向程序员的数据挖掘][1116]
- [流量劫持是如何产生的？][1117]
- [基于Spring可扩展Schema提供自定义配置支持][1118]
- [Coroutine in Java - Quasar Fiber实现][1119]
- [中国的支付清算体系是怎么玩的？][1120]
- [秒杀系统架构分析与实战][1121]
- [滴滴passport设计之道:帐号体系高可用的7条经验](https://mp.weixin.qq.com/s?__biz=MzAwMDU1MTE1OQ==&mid=2653547482&idx=1&sn=13675fae5e037d720a9e9fb4a4861afd&scene=1&srcid=0823uqCZQB4ZorkL0lZfpy7J&key=cf237d7ae24775e8e6b3106e6a2db91dbc3333bb81e65f277ef44396816795338c580626207f6e1774f5c9b8ca0f3fc1)

[1]: https://mp.weixin.qq.com/s?__biz=MzA5Nzc4OTA1Mw==&mid=2659597908&idx=1&sn=99bfd221634b539c08bf81cf0bf9e810&scene=1&srcid=0808ZZzPbMthTfzdUo7uMIfi&key=8dcebf9e179c9f3a8a1e453fca92b487f7c9c61780053719adbc5841a0451c6040eefe04ff38fce1982d8859a5e75383&ascene=0&uin=MzM1OTYzMjk1&devicetype=iMac%20MacBookAir7,2%20OSX%20OSX%2010.11.6%20build%2815G31%29&version=11020201&pass_ticket=544pih5rM0fs390LHFij67Kmi%2bqqmx1%2brpl43MnWwprR8JivDnzRcAYoqPryDLMk
[10]: https://mp.weixin.qq.com/s?__biz=MzI4NzE1NTYyMg==&mid=2651101480&idx=1&sn=dca99936779611b04bf2136616539625&scene=0&key=8dcebf9e179c9f3a199d9518da693cde7a912123ff73cf073cd4f322c5ef6e68e54a80eae522eda82610a6a997ec8efa&ascene=0&uin=MzM1OTYzMjk1&devicetype=iMac%20MacBookAir7,2%20OSX%20OSX%2010.11.6%20build%2815G31%29&version=11020201&pass_ticket=544pih5rM0fs390LHFij67Kmi%2bqqmx1%2brpl43MnWwprR8JivDnzRcAYoqPryDLMk
[111]: http://tech.meituan.com/performance_tuning_pattern.html
[1110]: https://mp.weixin.qq.com/s?__biz=MzA5NzkxMzg1Nw==&mid=2653159940&idx=1&sn=8dae7a9184290fcc164fc9afe46ee78f&scene=1&srcid=0629y6BPCB62CZehWrcvyarf&key=77421cf58af4a65336c8a5797d80d99d14ef02228301c56dcc7a048015f321dcffb8525784ddfe6a5371150509a96b77&ascene=0&uin=MzM1OTYzMjk1&devicetype=iMac%20MacBookAir7,2%20OSX%20OSX%2010.11.5%20build%2815F34%29&version=11020201&pass_ticket=reLjWX06MNg8boh2GDAogt6aXjJhCmG9b29pMBA7VKLp8y%2bDdvgoPYdK9wdqgr89
[1111]: http://www.infoq.com/cn/articles/coreos-analyse-etcd
[1112]: http://coolshell.cn/articles/10910.html
[1113]: http://mp.weixin.qq.com/s?__biz=MjM5MDE0Mjc4MA==&mid=503509249&idx=1&sn=44fbaff1e0fc0b5e8a8f8ad9585086f0#rd
[1114]: http://www.biaodianfu.com/redis-vs-memcached.html
[1115]: http://toutiao.com/i6295147863949181442/
[1116]: https://www.gitbook.com/book/wizardforcel/guide-to-data-mining/details
[1117]: https://mp.weixin.qq.com/s?__biz=MjM5NTc1NTU5NQ==&mid=2649839455&idx=1&sn=a06231c9d156f1d802cd0fcaf953e480&scene=1&srcid=0718IokidMhvfy3P9acLxpWX&key=77421cf58af4a653c9df2196be3c199abf2ce25cf5dac14e5bbb63efcd7d0741ba4266ae3da98a47a39ce0d5957dab42&ascene=0&uin=MzM1OTYzMjk1&devicetype=iMac%20MacBookAir7,2%20OSX%20OSX%2010.11.5%20build%2815F34%29&version=11020201&pass_ticket=iSWs4JAcjK2O2QG03PcIsMFCC8KdOBCcGgSn0QmM/MR3EEy8JD9XdzBKRRibMsdw
[1118]: http://blog.csdn.net/cutesource/article/details/5864562
[1119]: https://segmentfault.com/a/1190000006079389?from=groupmessage&isappinstalled=0
[112]: http://www.infoq.com/cn/articles/cap-twelve-years-later-how-the-rules-have-changed
[1120]: https://zhuanlan.zhihu.com/p/21249493?refer=cainiao
[1121]: https://mp.weixin.qq.com/s?__biz=MzIyNjE4NjI2Nw==&mid=2652557005&idx=1&sn=d92465682845c4f07254f6ce28b72abf&scene=1&srcid=0808hIhEFmZw1NkrF0CpKXHw&key=8dcebf9e179c9f3a22a82f12d75648fe681af6f97401ec36a8415948afa1d8998d129c3f4a4ece40634b08a8dc3caa92&ascene=0&uin=MzM1OTYzMjk1&devicetype=iMac%20MacBookAir7,2%20OSX%20OSX%2010.11.6%20build%2815G31%29&version=11020201&pass_ticket=544pih5rM0fs390LHFij67Kmi%2bqqmx1%2brpl43MnWwprR8JivDnzRcAYoqPryDLMk
[113]: http://coolshell.cn/articles/10910.html
[114]: http://tech.meituan.com/serialization_vs_deserialization.html
[115]: http://wenku.baidu.com/view/be946bec0975f46527d3e104.html
[116]: http://tech.meituan.com/avalanche-study.html
[117]: https://www.google.com.hk/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&ved=0ahUKEwjJ1p6517jNAhVBkpQKHbISADgQFggcMAA&url=https://raw.githubusercontent.com/bboyfeiyu/android-tech-frontier/master/software-architecture-patterns/%25E8%25BD%25AF%25E4%25BB%25B6%25E6%259E%25B6%25E6%259E%2584%25E6%25A8%25A1%25E5%25BC%258F.pdf&usg=AFQjCNHdRP-sWDnGP3QNdNLV_J-6AyB4RA
[118]: http://www.ituring.com.cn/article/5486
[119]: http://zqhxuyuan.github.io/2015/08/25/2015-08-25-Cassandra-Architecture/
[2]: https://mp.weixin.qq.com/s?__biz=MzI3MzEzMDI1OQ==&mid=2651814702&idx=1&sn=cafc4aa95db9cfdbd0373d00c633a8fb&scene=0&key=8dcebf9e179c9f3a30a085d0a66d12538c69388d48ec10cec73d8c2a63c63618593de5352444c25c785d7052f729de9f&ascene=0&uin=MzM1OTYzMjk1&devicetype=iMac%20MacBookAir7,2%20OSX%20OSX%2010.11.6%20build%2815G31%29&version=11020201&pass_ticket=544pih5rM0fs390LHFij67Kmi%2bqqmx1%2brpl43MnWwprR8JivDnzRcAYoqPryDLMk
[3]: https://mp.weixin.qq.com/s?__biz=MzAwMDU1MTE1OQ==&mid=2653547643&idx=1&sn=c06dc9b0f59e8ae3d2f9feb734da4459&scene=1&srcid=0808VntjzjTG8hSs7lIMCltG&key=8dcebf9e179c9f3a268d1062e3ac1663e55fe2f106053238be109273166d419bee0a70b36b87740d6452829021c5a73b&ascene=0&uin=MzM1OTYzMjk1&devicetype=iMac%20MacBookAir7,2%20OSX%20OSX%2010.11.6%20build%2815G31%29&version=11020201&pass_ticket=544pih5rM0fs390LHFij67Kmi%2bqqmx1%2brpl43MnWwprR8JivDnzRcAYoqPryDLMk
[4]: https://mp.weixin.qq.com/s?__biz=MzI3MzEzMDI1OQ==&mid=2651814734&idx=1&sn=e432a6739cb490229c7704d8d4887fa8&scene=1&srcid=08086vQ7WR40TXe6U1tlBwKU&key=8dcebf9e179c9f3ae5cebde1ac406b26591f8f136b5a943b0ba03a2072d07e4d2d484bf1e084673eac036250443977af&ascene=0&uin=MzM1OTYzMjk1&devicetype=iMac%20MacBookAir7,2%20OSX%20OSX%2010.11.6%20build%2815G31%29&version=11020201&pass_ticket=544pih5rM0fs390LHFij67Kmi%2bqqmx1%2brpl43MnWwprR8JivDnzRcAYoqPryDLMk
[5]: https://mp.weixin.qq.com/s?__biz=MzI1NDM2Nzg5Mw==&mid=2247483691&idx=1&sn=f00f98591c53b5754a7093509644fa19&scene=1&srcid=0808LSWWzTEn9TMShGvi2ugx&key=8dcebf9e179c9f3a01587e8c339789409c950ce169bd4a52e2a8ac578b5c26bfb6420676df75e4cecdb5af2427685c0b&ascene=0&uin=MzM1OTYzMjk1&devicetype=iMac%20MacBookAir7,2%20OSX%20OSX%2010.11.6%20build%2815G31%29&version=11020201&pass_ticket=544pih5rM0fs390LHFij67Kmi%2bqqmx1%2brpl43MnWwprR8JivDnzRcAYoqPryDLMk
[6]: https://mp.weixin.qq.com/s?__biz=MjM5MzYzMzkyMQ==&mid=2649826299&idx=1&sn=5792d8a7414608c22de212cab112e76c&scene=1&srcid=0808Wqnv6ilhDHKf8jfgb8DW&key=8dcebf9e179c9f3a0bbfb60138ad94eaf778f4446bc192b06d62af3651b42691ae34010e1206273bc7455b7aa112b757&ascene=0&uin=MzM1OTYzMjk1&devicetype=iMac%20MacBookAir7,2%20OSX%20OSX%2010.11.6%20build%2815G31%29&version=11020201&pass_ticket=544pih5rM0fs390LHFij67Kmi%2bqqmx1%2brpl43MnWwprR8JivDnzRcAYoqPryDLMk
[7]: http://www.infoq.com/cn/presentations/a-long-period-of-atypical-jvm-gc-caused-by-os?utm_campaign=rightbar_v2&utm_source=infoq&utm_medium=presentations_link&utm_content=link_text
[8]: http://hellojava.info/?p=498&nsukey=LnMqovC7%2bJ%2bmpA5qa%2biAEf7RiFMU5pljJTzZPJwE8c8H4p1zyfptJXnOKgsTlMlvsAu/abXR77ymADDH9L3vgQ==
[9]: https://mp.weixin.qq.com/s?__biz=MzA5Nzc4OTA1Mw==&mid=2659597854&idx=1&sn=4e1d62535590b5e2233931a4ce996ca2&scene=1&srcid=0801lVUQr0CZCYgtuKETj3XD&key=8dcebf9e179c9f3a9f07c1b9eff1aac53ab6e919a4170d9d8793b785318135e91e1caa3d2017c793679213b47f389ace&ascene=0&uin=MzM1OTYzMjk1&devicetype=iMac%20MacBookAir7,2%20OSX%20OSX%2010.11.6%20build%2815G31%29&version=11020201&pass_ticket=544pih5rM0fs390LHFij67Kmi%2bqqmx1%2brpl43MnWwprR8JivDnzRcAYoqPryDLMk
