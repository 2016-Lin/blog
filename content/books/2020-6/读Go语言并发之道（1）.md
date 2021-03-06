---
title: "读Go语言并发之道（1）"
date: 2020-06-13T11:10:50+08:00
draft: false
toc: true
categories: ["图书"]
series: ["golang并发编程"]
tags: ["图书","go","并发编程"]
toc: true
---

#### 导读
以前阅读完《Go语言并发之道》这本书，感悟许多，现在因为对于golang并发的需要，并且发现自己对于并发相关的知识还了解不足，现在重新来读这本书，并在这里记录下，我通过阅读这边图书的收获知识。

#### 并发和并行的区别

在现代编程中，通常我们都会遇到这两个词，“并发”和”并行“两个概念，并发:一般指的是在多核CPU中，同时能运行的任务，例如，我有一个2核CPU表示，我在同一时间，能同时处理两个任务，而并发表示，在一定时间内，我能处理的任务数，例如，单核CPU通常可以放歌和浏览网页，在我们看来，它们好像是同时运行的但是他们是被CPU调度运行的，也就是分时使用CPU。

并发和并行产生的原因，在以前，CPU的往往是单核的，CPU的设计符合摩尔定律的发展，CPU的性能能够跟的上业务和技术的发展，为了适应同时运行任务的需要，CPU设计就需要满足在不同的时间运行不同的任务，达到同时运行的效果。然后随着摩尔定律的失效，以及需求和技术的不断发展，人们从多核CPU进行设计，多核CPU就能同时运行多个任务。

因此并发先于并行出现。在单核CPU时代，为了适应同时运行任务的需求，出现了并发，在多核时代，为了更好的利用CPU和业务的需要，出现了并行。

在现在编程中，往往是并行和并发同时存在的。

#### Go的并发模型和调度模型

Golang实现了两种并发形式，一种是在java和python中非常普遍的：多线程共享内存，另一种就是Go语言中特有的，

