---
title: boost/mutex笔记
date: 2018-04-07 18:15:14
tags: 
 - thread tool
 - mutex
 - boost
categories:
 - Programming Languages
 - C++
---
# 说明

本文主要记录一下boost中mutex的特点。

<!-- more -->
# 第一部分

该部分介绍boost::mutex，boost::shared_mutex，boost::unique_lock和boost::shared_lock。

boost::mutex是最简单的锁，它提供了lock和unlock两种方法。 lock代表线程要占用资源，unlock代表释放对资源的占用。如果当前线程lock一个已经被lock过的资源，则会阻塞直到资源被unlock。

boost::shared_mutex不仅有lock和unlock方法，还有shared_lock和shared_unlock方法，当资源被线程shared_lock的时候，其他线程依然可以shared_lock线程，当需要相应次数的shared_unlock才能完全释放资源。作用场景：当访问资源时，可以多个线程同时访问，所以可以使用shared_lock和shared_unlock来保证性能；当修改资源时，多个线程同时操作会有可能发生错误，所以使用lock和unlock方法比较合适。

在具体操作时，为了避免疏忽导致资源lock后忘记unlock或者因为异常没有unlock导致死锁，boost库提供了boost::unique_lock和boost::shared_lock。其中boost::unique_lock在构造的时候传入一个mutex的引用，并调用lock()方法，在析构的时候调用unlock()方法。boost::shared_lock在构造的时候传入mutex的引用，并调用shared_lock()方法，在析构的时候调用shared_unlock()方法，所以boost::shared_lock需要传入一个boost::shared_mutex。

