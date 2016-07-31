---
title: 使用hystrix保护你的应用
date: 2016-07-30T18:12:29.000Z
layout: post
subtitle: hystrix入门
author: kris.zhang
header-img: head.jpg
wechat_pig: wechat.jpg
mathjax: true
tags:
  - 框架
  - 服务降级
  - 熔断器
  - 资源隔离
  - 开源
  - hystrix
---

> 凡是可能出错的事必定会出错

![豪猪](hystrix-defend-your-webapp/hystrix.png)

hystrix(`[hɪst'rɪks]`)是豪猪的意思。豪猪是一种哺乳动物，全身是刺用以更好的保护自己。netflix使用这畜生来命名这框架实在是非常的贴切，意味着hystrix能够像豪猪的刺一样保护着你的应用。下面是一张豪猪的`高清无码大图`。

![豪猪](hystrix-defend-your-webapp/豪猪.jpg)

本文专门探讨netflix的hystrix框架。首先会说明在一次请求中调用多个远程服务时可能会出现的致命的雪崩问题，然后提出几个解决这些问题的办法，从而引出了`hystrix`框架；之后我们会给出几个例子试图说明hystrix是如何解决上述雪崩问题的，同时还会给出其常用配置的解释和额外的使用示例，从而使得读者能够从一个更加宏观角度去理解hystrix究竟都能做什么；然后我们将会深入框架内部，看一看hystrix的设计思想及其实现原理。最后我们再来看一看如何对你的线程池进行监控、如何进行配置调优等。

<!-- toc -->

 # 从雪崩看应用防护

## 一个现实中常见的场景

我们先来看一个分布式系统中常见的简化的模型。此图来自hystrix的[官方wiki](https://github.com/Netflix/Hystrix/wiki)，因为模型比较简单我这里就在不在重复画图，直接使用现成的图片做补充说明。

![一个简单的模型](hystrix-defend-your-webapp/hystrix_soa1.png)

App Container可以是我们的应用容器，比如`jetty`，`tomcat`，也可能是一个用来处理外部请求的线程池（比如netty的worker线程池）。一个用户请求有可能依赖其他多个外部服务，比如上图的A,H,I,P，在不可靠的网络环境下，任何的RPC都可能会面临三种情况：成功、失败、超时。如果一次用户请求所依赖外部服务A,H,I,P有任何一个不可用，就有可能导致整个用户请求被阻塞。考虑到应用容器的线程数目基本都是固定的（比如tomcat默认200线程数），当在高并发的情况下，一个外部服务的超时，就有可能使得整个线程池被占满，这是[长请求拥塞反模式](http://tech.meituan.com/performance_tuning_pattern.html)。

![长请求拥塞反模式](hystrix-defend-your-webapp/hystrix_soa2.png)

更进一步，线程池被占满会导致整个服务不可用，而依赖该服务的其他服务，就又可能会重复产生上述问题。因此整个系统就像雪崩一样逐渐的扩散、坍塌、崩溃了！

## 产生原因

服务提供者不可用，从而导致服务调用者线程资源耗尽是产生雪崩的原因之一。除此之外还有其他因素能够产生雪崩效应：

- 服务调用者自身流量激增，导致系统负载升高。比如异常流量、用户重试、代码逻辑重复
- 缓存到期刷新，使得请求奔向数据库，导致长请求拥塞
- 重试机制，比如我们`rpc`框架dubbo/motan的retry次数，每次重试都可能会恶化服务提供者
- 硬件故障，比如机房断电，电缆被挖了....

## 常见的解决方案

针对上述雪崩情景，有很多应对方案，但没有一个万能的模式能够应对所有情况。

1. 针对服务调用者自身流量激增，我们可以采用autoscaling方式进行自动扩容以应对突发流量，或者在负载均衡器上安装限流模块。参考[微博：春节日活跃用户超一亿，探秘如何实现服务器分钟级扩容](https://yq.aliyun.com/articles/18132?spm=5176.blog7548.yqblogcon1.8.sohzos)
2. 针对缓存到期刷新，我们也有很多方案，参考[Cache应用中的服务过载案例研究](http://tech.meituan.com/avalanche-study.html)
3. 针对重试机制，我们可以关闭重试，直接采用`failfast`，或者采用`failsafe`进行优雅降级。
4. 针对硬件故障，我们可以做`多机房容灾`，`异地多活`等。

hystrix也能够解决雪崩问题，不过他所能解决问题的场景是`服务提供者不可用`（包括服务提供者超时，失败，以及网络连接故障）。hystrix主要提供了以下两种机制保护你的应用：

1. 资源隔离机制（线程隔离、信号量隔离）
2. 熔断器

为了方便编程，hystrix采用命令模式+继承方式提供给用户更灵活的编程模型，下面我们就来看如何使用hystrix。

# 使用hystrix

## 我的系统4个9

## 从简单例子入手

## 使用优雅降级

## 正确选择隔离模式

## 开启circuit-breaker

## 使用request-cache

## 使用collapse

# hystrix核心实现

## 隔离机制实现

## 熔断器实现

## metrics实现

# 监控和调优

## 单机监控和集群监控

## 如何进行参数配置

# 后记

在写这篇文章之前，我犹豫了很久，反复阅读了wiki文档和相关资料，觉得wiki文档已经写的非常全面了，这让我无从下笔：因为你的文章中任何一点都可以在官方wiki上找到影子。所以似乎你写出来的东西是没有太大意义的。但我在谷歌上搜了很多关于hystrix的中文文章，发现大家都是千篇一律的翻译官方文档，有些是半翻译半记录，没有太多自己的思考。因此我决定写一篇集入门、应用、实现原理、监控的

## 参考资料

- [hystrix wiki](https://github.com/Netflix/Hystrix/wiki)
- [防雪崩利器：熔断器 Hystrix 的原理与使用](https://github.com/Netflix/Hystrix/wiki)
- [hystrix文档译文](http://youdang.github.io/categories/%E7%BF%BB%E8%AF%91/)
- [性能优化模式](http://tech.meituan.com/performance_tuning_pattern.html)
