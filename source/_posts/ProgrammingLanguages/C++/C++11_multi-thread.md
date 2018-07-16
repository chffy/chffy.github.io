
---
title: C++11 multi-thread
date: 2018-07-10 16:28:59
tags:
 - thread tool
 - c++11
categories:
 - Programming Languages
 - C++
---
# Description

This blog introduce some multi-thread tools of C++11.

<!-- more -->
# Overview
**lock tools**: mutex, unique_lock, lock_guard
**thread tools**: thread, future, package_task
**thread switching tools**: condition_variable
**function tools**: lambda, bind

In multi-thread program, using **lock tools** to lock code, using **thread tools** to alloc/manage thread, using **switching tools** to achieve multi-thread switch, using **function tools** can simply code.

# Lambda
**format**： [capture list] (parameter list) -> return type { function body }
**example**:
```c++
int exparam = 3;
auto func = [exparam](double a, double b) -> int {
	return a + b + exparam;
};
std::cout << func(1, 2.1) << std::endl; // output will be 6. 
```
In some situation, we can simply lambda like:
```c++
auto func = [] { return 3; };
```

# mutex and Lock
```c++
#include <mutex>
```
**std::mutex** is synchronization primitive to protect data from multi-thread access. It's base method is lock and unlock, only one thread can own a mutex object in the same time. 
std::lock_guard, 构造参数为mutex，在构造的时候调用lock，析构的时候unlock。
std::unique_lock，构造参数为mutex，和lock_unique的主要区别是：在拥有lock_guard的功能基础上，可以自己控制lock/unlock，且可以和其他unique_lock对象交换状态。

# condition_variable
include <condition_variable>
std::condition_variable, 同步原语, 有方法：notify_one, notify_all, wait, wait_for, wait_util
wait相关函数，需要传入一个unique_lock，在wait的过程中暂时释放锁，等有notify事件产生，再取回锁的使用权。

# 线程
include <thread>
std::thread, 构造参数为func, f_param1, f_param2, ..., 其中func是函数，f_param是函数需要的参数。
