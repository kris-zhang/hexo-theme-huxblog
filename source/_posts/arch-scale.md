---
title: 《架构真经》读书笔记
date: 2018-12-17 22:36:33
author: kris.zhang
header-img: head.jpg
tags: 
  - 架构
---

## 大道至简

我学到了几点思路：

① 5个原则，其实说白了就是要方案简单。其中过渡设计有几个例子举得比较好，你可以用来喷人，比如你说PD，你这个方案太复杂，过渡设计，就像你设计支持100度的空调一样。

② DID原则，设计、实施、部署，层层递进，设计的时候考虑很多，可以随便脑暴，把未来规划好，但是实施（写代码）的时候，我们就要用最简单的方案，之后部署的时候，我们只要最低部署成本，随着业务量增加，则慢慢线性扩展。

这个原则很重要，我们在设计系统的时候，一定要面向未来去考虑。

③ 几个技术点，一是减少域名解析，而是减少页面（合并加载），同构网络（不要以为有了协议，就能为所欲为，有了协议，同时有不同实现的话，兼容性成为灾难），浏览器并发连接数

这章告诉我们设计架构，一定要尽可能的简单，下次再有人过渡设计，用这个原则去怼他们。

## 分而治之

这里我学到了一个，伸缩立方体。集成了一些水平扩展的技术思路。xyz轴，x轴即水平扩展，我理解其实就是scale out，一个负载均衡后面，可以直接扩展机器。或者读写分离，多加读机器；y轴，我理解是垂直拆分，就是soa或者微服务化，将一个业务拆分为多个子业务，直接通过RPC调用；z轴就比较高级了，可以理解为蚂蚁的用户水平拆分或者逻辑zone的概念，这种概念可以将用户（或者别的什么东西）按照某个原则分成多个。每个部分都是独立部署单元，每个部署单元，都是一个小型的蚂蚁金服。这样带来的好处是容灾能力大大增强

## 水平扩展

几个原则，一个是类似谷歌分布式系统的原则一样，用便宜廉价的大量小机器代替高性能昂贵的机器。其二是利用多数据中心，如果不能自建则用公有云或私有云（云主要用来所伸缩弹性计算）。这个一般公司涉及不到，类似阿里，蚂蚁等会有这些东西。美团应该也有。

多数据中心的问题是数据跨机房复制。

## 先利其器

本章给我的最大收获之一是，在进行数据架构设计的时候，一定要对你的数据结构，数据量，读写比，访问量，是否是强事务等做一个全面的评估，再去选择合适的存储系统，这样不但能够使你的系统后期扩展性更强，也能够减少成本。

所以对于架构师来讲，你要了解各种存储系统的成本差异、技术实现细节差异等等。诸如文件系统、rdb、nosql（表格存储、键值存储、文档存储）、newsql、图数据库、位图数据库、时序数据库，等等。你都需要了解。

## 画龙点睛

两个我觉得有用的原则，其一是永远不要写后读。这个一定要记得，尤其是在读写分离场景，很大概率你读到的是旧数据，还有一种场景是你可能很少遇到的，但也算是写后读。定时回调读+写。比如我注册一个定时回调器，这个回调代码中会查询数据x，然后做一些动作。但在回调代码执行之前执行了写x的操作，而后马上到达定时时间，此时就会发生写后读。

当然写后一定要读的场景，我们也可以通过其他方案解决，比如加入缓存，或者直接返回bean（insert之前的原始数据）等等，如果一定要校验（比如有监管问题），那么可以采用异步日志的方式，而不要阻塞用户线程。

第二个原则是放宽时间约束，其实我们最常见的场景就是要最终一致性方案，这个是舍弃实时，变为准实时，甚至是t+h或t+1等等。其实除了这个场景，我这里还有一个放宽约束的场景，比如到一个时间点给用户发某些东西（优惠、短信、push通知）等等，一种解决方案是采用状态+时间+读方案，但是这无法主动触发；另一个方案是定时器，但是定时器有一个问题，时间精度总不是那么精确，在加上系统稳定性等因素，总会有一定的延迟，此时怎么做呢？可以在产品规则上做一些调整，比如不要那么精确，例如：12：00你可以说12：00-12：30之前送达。这种也是放宽时间约束的一种办法。

## 缓存为王

不想多啰嗦，没什么新东西

## 前车之鉴

蚂蚁金服有三板斧，可回滚、可监控、可灰度。任何发布，任何变更必须可回滚、可监控、可灰度。这个是原则问题。

关于知识的深度和广度，作者有一个深度多问why，广度也要考虑人员、管理、流程。这两点比较有收获。深度可以通过多问why，刨根问底，自然深度就慢慢有了，都没有必要专门去读有深度的书（有可能你读不懂，浪费时间），针对具体事情，你把他深挖，就够你用的了。广度一般我们都以为各种新技术啥的，其实不全是，你还要看人员（比如产品运营等，你也要深入了解他们的思维和工作），管理（你要学习管理学，如何跟人打交道等），流程（如何优化现有流程，如何能更好的优化资源利用，如何能合理排期等）

关于复盘，有一个比较好的流程：时间轴，你先梳理问题发生的时间线索；明确问题，你多问why，找到哪里除了问题；确定方案，最后至少要给出一个方案，并且这个方案是符合SMART原则的。具体的、可度量、可实现的、现实的、有时间性的。

## 重中之重

主要讲db使用上的一些注意事项。比如，不要写存储过程，尽量不要连表，不要select * ，谨慎使用行锁，不要用两阶段提交等等。其实我觉得这章没啥意思，很多讲mysql的书都有这些经验，而且讲的更全面和细致。这里姑且算作者以自身经验作了一次汇总吧。

## 有备无患

本章主要讲可用性对可扩展性的影响。有几个观点，故障隔离永道+开关+放单点故障（SPOF），其中SPOF这个英文缩写得记得，比较牛逼，拿出去显得很专业。另外泳道隔离其实无处不在。比如线程池中的每个线程是隔离的，每台服务器都是隔离的（彼此不影响），集群是隔离的，机房是隔离的，等等。其中故障隔离的几个原则挺不错的，可以用来说服别人：1，不要相互依赖，独立工作，2，减少异步调用。其实说白了就是尽量降低他们的相关系数，cov(x,y)=0，让其不相关，这样故障概率就可以做到p(x)*p(y)，即最消化故障概率。

另外，书中用电路图类比架构，我觉得这个思想很有意思，很形象，以后你在跟别人讲架构的时候，可以用来借鉴。串联架构，并联架构等等。流量入口就像电池一样。

## 超然物外

主要讲无状态服务。举两个无状态服务的例子。一是map-reduce的处理，写map或者reduce方法，使用函数编程方式，要保证无状态，同时要无副作用等，相同参数一定有相同输出。其二是保存用户session的例子，如果session存在缓存服务器，则是有装填，你需要维护他们，如果放到cookie，服务端只去校验，session服务用于生成cookie，则就变成无状态服务。

如果一定要使用会话状态，则考虑使用分布式缓存，蚂蚁就是这么做的，通过分布式缓存tair，来存储session。

## 异步通信

本章后半部分的内容过于理想化了，尤其最后的那个成本-价值四象限，其实维度单一，而且没有考虑人性（大部分人都是低估成本，高估价值）。所以没有参考性。

异步通信这块，是属于架构中最基本内容。同步转异步，增加性能，但是会带来复杂性。这个其实不用做多说明，你就看是否是强弱依赖。强依赖基本都要走同步，弱依赖基本都可以走异步。然后再考虑性能因素，削峰蓄洪，得用队列。

消息队列扩展这里，其实一般做法都是垂直扩展，分租户啊，分业务啊，2-8原则啊等等。按照topic划分。

## 意犹未尽

几点，一是防止被供应商遏制咽喉（这里一般是CTO决策层了）。而是分级存储+分级处理负载。这个比较有用，分级存储主要看你数据的价值+访问频次。有一个价值+成本曲线，这个值得学习，也是架构师成本收益思维的一个典型应用。其二是分级处理负载，这个比如阿里搞的离线在线混部等等。不同业务类型用不同的机器等。

完善监控，这个也是架构师必须知道的，甚至是常识。无论怎么样的系统，都一定要有监控，甚至监控系统也要有自己的监控。至于监控的维度，内容，思想，则都是经验积累了。

保持竞争力。。。这个就虚了点。因为竞争力是更成本有关系的。你要保持竞争力，必然要投入成本。所以不是想保持就保持的。也要有投入产出比。核心技术，一定要保持竞争力，成本投入到这里。非核心技术，作为公司影响力和技术形象的一种，类似公益活动。。

总结，不否定本书作者能力以及本书价值。对于国内大部分读者来讲，应该是读不懂的，因为毕竟这本书是站在一个更高的层次来写的，面向的都是CTO或者大公司总监，至少经历过公司基础设施从零到有的过程。有些思想很值得借鉴，比如AKF矩阵，关于深度广度的思考等等。有些则比较过时了，比如cookie大小问题（其实可以采用localStorage），比如现在早都已经进入移动互联网时代了，还在讨论web的相关技术等等，让我觉得，其实中国技术圈从实战到工程理论，已经不比硅谷那帮子工程师差多少了。想想每年的双十一，618等大促，我们的见识已经不在浅薄，工程技术能力，已经不在落后，甚至超过了美国的很多大公司。但中国的计算机基础研究，还是很薄弱，尤其是在对理论算法和行业标准制定上落后很多。工程能力强也只是一个方面的体现罢了。