---
title: 2016精选文章推荐
date: 2016-08-09T14:01:43.000Z
subtitle: 8月15日-8月22日
layout: post
author: kris.zhang
header-img: head.jpg
wechat_pig: wechat.jpg
mathjax: true
tags:
  - 精选文章推荐
---

> 越来越需要过滤的本质是因为信息爆炸，而过滤的本质应该是一种分类。越精细，就越准确，效果也就越好，个性化也就越强，也这能够解释为什么推荐系统越来越流行的原因。

![head](articles2016/wechat.jpg)

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
