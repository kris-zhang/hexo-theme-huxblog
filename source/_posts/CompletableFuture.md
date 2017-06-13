---
title: CompletableFuture学习笔记
date: 2017-06-11T19:13:08.000Z
layout: post
author: kris.zhang
header-img: head.jpg
tags:
  - jdk8
  - JCU
---

> 关于CompletableFuture，网上有大量的文章讲解这个JDK8中新出的类。但这些文章大多作为一种学习札记，文章组织逻辑，代码示例也基本没有考虑到读者的阅读体验。本文试图用一个例子进行贯穿的讲解，同时避免无意义的示例代码，使读者更容易去记忆和使用CompletableFuture。

本文主要内容如下：

- CompletableFuture基本简述
- API分类与记忆规律
- 创建CompletableFuture
- 取值与状态测试
- 控制CompletableFuture执行
- CompletableFuture行为接续

## CompletableFuture基本简述

首先，我们可以用一个生活中的例子去理解异步的相关概念。我们将一组算法封装成一个函数，这个函数的本质也可理解为一种**行为**，比如我们做蛋糕这一行为。行为有可能是有结果的，也有可能仅仅是执行一段逻辑，但没有结果。比如我们做出了蛋糕，蛋糕即是行为结果。有结果的行为，我们用`Callable`句柄加以描述；无结果的行为，我们用`Runnable`句柄加以描述。假如，我们不自己做蛋糕，而是委托给糕点师去做，这样我们便可以做些别的事情（比如去热杯牛奶）。那么我们把‘委托给糕点师’这个行为使用`Future`句柄去描述，它表示蛋糕会在‘未来’由糕点师做好，而不是现在。于是我便可以拿着这个句柄去热杯牛奶喝了，同时，我也能随时通过这个句柄询问糕点师：你做好了没有？

没事儿总去问糕点师你做好了没有，很是麻烦。最好当糕点师做好了之后，能主动告诉我们。在jdk8以前，我们只能自己封装，或者使用三方类库（比如`Guava`的`ListenableFuture`）。作为牛逼闪闪的JDK，怎能甘于寂寞？于是同步大师`Doug Lea`在JDK8中编写了`CompletableFuture`，使用他便能够提前跟糕点师打好招呼：你做完蛋糕告诉我一声，老纸好去吃早餐。

因此Callable、Runnable、Future、CompletableFuture之间的关系一目了然：

- Callable，有结果的同步行为，比如做蛋糕，产生蛋糕
- Runnable，无结果的同步行为，比如喝牛奶，仅仅就是喝
- Future，异步封装Callable/Runnable，比如委托给师傅（其他线程）去做糕点
- CompletableFuture，封装Future，使其拥有回调功能，比如让师傅主动告诉我蛋糕做好了

如下代码示例

```java
public static void main(String[] args) throws InterruptedException {
        CompletableFuture
            //委托师傅做蛋糕
            .supplyAsync(()-> {
                try {
                    System.out.println("师傅准备做蛋糕");
                    TimeUnit.SECONDS.sleep(1);
                    System.out.println("师傅做蛋糕做好了");
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
                return "cake";
            })
            //做好了告诉我一声
            .thenAccept(cake->{
                System.out.println("我吃蛋糕:" + cake);
        });

        System.out.println("我先去喝杯牛奶");
        Thread.currentThread().join();
    }
```

## API分类与记忆规律

CompletableFuture的api有50几个，我们可以先将其划分为若干大类：

**创建类：用于CompletableFuture对象创建，比如：**

- completedFuture
- runAsync
- supplyAsync
- anyOf
- allOf

**状态取值类：用于判断当前状态和同步等待取值，比如：**

- join
- get
- getNow
- isCancelled
- isCompletedExceptionally
- isDone

**控制类：可用于主动控制CompletableFuture完成行为，比如：**

- complete
- completeExceptionally
- cancel

**接续类：CompletableFuture最重要的特性，用于注入回调行为，比如：**

- thenApply, thenApplyAsync
- thenAccept, thenAcceptAsync
- thenRun, thenRunAsync
- thenCombine, thenCombineAsync
- thenAcceptBoth, thenAcceptBothAsync
- runAfterBoth, runAfterBothAsync
- applyToEither, applyToEitherAsync
- acceptEither, acceptEitherAsync
- runAfterEither, runAfterEitherAsync
- thenCompose, thenComposeAsync
- whenComplete, whenCompleteAsync
- handle, handleAsync
- exceptionally

上面的方法非常多，而大多具有相似性，我们大可不必马上记忆。先来看看几个一般性的规律，便可辅助记忆（重要）：

1. 以Async后缀结尾的方法，均是异步方法，对应无Async则是同步方法。
2. 以Async后缀结尾的方法，一定有两个重载方法。其一是采用内部forkjoin线程池执行异步，其二是指定一个Executor去运行。
3. 以run开头的方法，其方法入参的lambda表达式一定是`无参数`，并且`无返回值`的，其实就是指定Runnable
4. 以supply开头的方法，其方法入参的lambda表达式一定是`无参数`，并且`有返回值`，其实就是指Supplier
5. 以Accept为开头或结尾的方法，其方法入参的lambda表达式一定是`有参数`，但是`无返回值`，其实就是指Consumer
6. 以Apply为开头或者结尾的方法，其方法入参的lambda表达式一定是`有参数`，但是`有返回值`，其实就是指Function
7. 带有either后缀的表示谁先完成则消费谁。

以上6条记住之后，就可以记住60%以上的API了。

## 创建CompletableFuture

创建CompletableFuture，其实就是我们将做蛋糕这个事情委托糕点师。我们怎么委托呢？其一是我们要指定‘做蛋糕’这个事情（Runnable,Supplier），其二是指定糕点师（ExecutorService或内部默认的ForkJoinPool）。除此之外，我们也可能委托多个事情，比如：做蛋糕、热牛奶等等，因此我们也可以将这些委托通过`allOf`或者`anyOf`进行组合。

```java
        // 直接创建
        CompletableFuture c0 = new CompletableFuture();

        // 直接创建一个已经做完的蛋糕
        val c1 = CompletableFuture.completedFuture("cake");

        // 无返回值异步任务，会采用内部forkjoin线程池
        val c2 = CompletableFuture.runAsync(()->{});

        // 无返回值异步任务，采用定制的线程池
        val c3 = CompletableFuture.runAsync(()->{}, newSingleThreadExecutor());

        // 返回值异步任务，采用定制的线程池
        val c4 = CompletableFuture.supplyAsync(()-> "cake", newSingleThreadExecutor());

        // 返回值异步任务，采用内部forkjoin线程池
        val c5 = CompletableFuture.supplyAsync(()-> "cake");

        // 只要有一个完成，则完成，有一个抛异常，则携带异常
        CompletableFuture.anyOf(c1, c2, c3, c4, c5);

        // 当所有的 future 完成时,新的 future 同时完成
        // 当某个方法出现了异常时,新 future 会在所有 future 完成的时候完成,并且包含一个异常.
        CompletableFuture.allOf(c1, c2, c3, c4, c5);
```

想要创建一个CompletableFuture，则可参考如上代码，需要有几点注意：

1. 创建一个已经完成的CompletableFuture有卵用？答，可作为默认值存在。
2. new出一个CompletableFuture有卵用？答，可通过完成控制api，灵活的控制其完成、异常时间点。

## 取值与状态测试

取值就是我们直接跑到糕点师那里眼巴巴的看着他做好，这种是同步方式。状态测试则是我们不断的询问糕点师你做好了没有，你做好了没有，这也是Future所支持的。

```java
        //不抛出中断异常，看着你做蛋糕
        //阻塞
        cf.join();

        //有异常，看着你做蛋糕
        //阻塞
        cf.get();

        //有异常，看着你做蛋糕一小时
        //阻塞
        cf.get(1, TimeUnit.HOURS);

        //蛋糕做好了吗？做好了我直接吃你做的，做不好我吃我的
        //非阻塞
        cf.getNow("my cake");

        // 我问糕点师：蛋糕是否不做了？
        //非阻塞
        cf.isCancelled();

        //我问糕点师：蛋糕是否做糊了？
        //非阻塞
        cf.isCompletedExceptionally();

        // 我问糕点师：蛋糕做完了吗？
        //非阻塞
        cf.isDone();
```

需要注意的是，使用`get()`方法，为了避免无限期的等待下去，产生大量的等待线程，应在实际应用中采用超时版本的`get()`，或者使用`getNow()`。


## 控制CompletableFuture执行

CompletableFuture有三个终结状态：完成、异常、取消。

```java
        // 蛋糕做完了
        cf.complete("cake");

        // 蛋糕做糊了
        cf.completeExceptionally(new RuntimeException());

        // 你别做蛋糕了。
        cf.cancel(false);
```

需要注意的是，cancel方法入参是没用的，你true也好，false也罢，均不生效，因为内部实现的时候，这参数根本没有用。这在jdk中算是奇葩之一了，好在注释写的清清楚楚的：

> @param mayInterruptIfRunning this value has no effect in this
> implementation because interrupts are not used to control
> processing.

## CompletableFuture行为接续

接续即是CompletableFuture存在的核心价值。接续分为以下几种：

1. CompletableFuture + (Runnable,Consumer,Function)
2. CompletableFuture + CompletableFuture
3. CompletableFuture + 结果处理

### 接续方式1，

说白了就是CompletableFuture执行完成之后(done)再执行我指定所的方法。如下实例：

```java
       val makeCake = CompletableFuture.supplyAsync(()->{
            System.out.println("糕点师做蛋糕");
            return "cake";
        });

        makeCake.thenApplyAsync(cake->{
            System.out.println("蛋糕做好了，我来做牛奶");
            return "milk";
        })
        .thenAcceptAsync(milk->{
            System.out.println("牛奶做好了");
            System.out.println("我开始吃早饭");
        })
        .thenRunAsync(()->{
            System.out.println("吃完早饭我去上班");
        });
```

### 接续方式2

如果本身做牛奶和做蛋糕已经是两个不同的CompletableFuture，我们可以使用接续方式2，

```java
        val makeCake = CompletableFuture.supplyAsync(()->{
            System.out.println("糕点师做蛋糕");
            return "cake";
        });

        val makeMilk = CompletableFuture.supplyAsync(()->{
            System.out.println("我来做牛奶");
            return "milk";
        });

        // 有参数-有返回值
        makeCake.thenCombineAsync(makeMilk, (cake, milk)->{
            System.out.println("蛋糕牛奶做好了，我在洗一个苹果");
            return "apple";
        });

        // 有参-无返回值
        makeCake.thenAcceptBothAsync(makeMilk, (cake, milk)->{
            System.out.println("蛋糕牛奶做好了，我开始吃饭");
        });

        // 无参-无返回值
        makeCake.runAfterBothAsync(makeMilk, ()->{
            System.out.println("蛋糕牛奶做好了，我开始吃饭");
        });

        // 谁快用谁，参数类型需要一样
        makeCake.applyToEither(makeMilk, (milkOrCake)->{
            System.out.println("蛋糕或牛奶做好了，我等不及洗一个苹果");
            return "apple";
        });
        
        // 谁快用谁，参数类型需要一样
        makeCake.acceptEitherAsync(makeMilk, (milkOrCake)->{
            System.out.println("蛋糕或牛奶做好了，我等不及先吃一个");
        });

        // 谁快用谁，参数类型需要一样
        makeCake.runAfterEitherAsync(makeMilk, ()->{
            System.out.println("蛋糕或牛奶做好了，我等不及先吃一个");
        });

```

或者我们亦可以采用compose直接接续两个CompletableFuture

```java

        makeCake.thenComposeAsync(cake-> CompletableFuture.supplyAsync(()->{
            System.out.println("我来做牛奶");
            return "milk";
        }));
```

### 接续方式3

如果我们只想做CompletableFuture结果处理，而不接续其他动作，那么我们可以采用接续方式3：

- whenCompleteAsync: 处理完成或异常，无返回值
- handleAsync：处理完成或异常，有返回值

```java
        val makeCake = CompletableFuture.supplyAsync(()->{
            System.out.println("糕点师做蛋糕");
            return "cake";
        });

        // 无返回值处理
        makeCake.whenCompleteAsync((cake, exception)->{
            if (exception != null) {
                System.out.println("蛋糕做糊了。。。。");
            } else {
                System.out.println("蛋糕做好了");
            }
        });

        // 有返回值处理
        makeCake.handleAsync((cake, exception)->{
            if (exception != null) {
                System.out.println("蛋糕做糊了。。。。出去买个现成的蛋糕");
                return "现成的蛋糕";
            } else {
                System.out.println("蛋糕做好了");
            }
            return cake;
        });

        // 只处理异常，只有阻塞调用。产生异常则会返回'出去买一个现成的蛋糕吧'
        makeCake.exceptionally(exception->{
            System.out.println("蛋糕做糊了。。。。出去买个现成的蛋糕");
            return "现成的蛋糕";
        });
```

## 参考资料

- [全文代码片段](https://gist.github.com/kris-zhang/d62853e90cfb72bbfc2a888b2dfcb784)
- JDK源码和javadoc。