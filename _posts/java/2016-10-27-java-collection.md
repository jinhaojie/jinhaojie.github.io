---
layout: post
title: java -- 容器简介
description: java
keywords: java
category : java
tags : [java , collect]
---
* 目录
{:toc}

---
## 简述
　　java容器（**Collection**），提供了完善的方法保存对象
## 一张图来描述容器的分类
<img  src="/assets/images/java/java-collection.jpg"  style="border: solid; align:center;"/>
<p style="font-weight: bold;" align="center">容器图谱</p>
## 具体容器的介绍

> #### Collection

Collection下面主要有三个容器 `List`, `Set`, 和`Queue`

##### List　（存放有序数据）

1. *ArrayList*
  * `底层数组实现，随机访问快，中间插入或删除慢.`
  * `线程不同步`
2. LinkedList
  * `底层链表实现，随机访问慢，曾删快`
  * `线程不同步`
  * `可以当做栈、队列、双端队列使用`
3. Vector
  * `底层数组实现，因线程同步而访问慢，新程序不该使用该容器`

##### Set　（不能存放重复元素，无序）

1. HashSet
  * `访问快`
2. LinkedHashSet
  * `以插入顺序保存元素`
  * `继承自HashSet，应用了Hash算法，所以访问也和HashSet有相同的效率`
3. TreeSet
  * `红黑树实现，保证了顺序`

##### Queue (队列)
1. LinkedHashSet
   * `LinkedHashSet提供了对Queue和Stack的支持`
2. PriorityQueue
   * `维护一个堆`
   * `通过Comparator来修改优先级,默认是按自然顺序`


> #### Map

map存放键值对。

1. HashTable
  * `同步的,现在已经基本不使用`
2. HashMap
  * `非同步`
3. LinkedHashMap
  * `非同步`
  * `按插入顺序保留键,有HashMap的速度`
　　　　
4. TreeMap
  * `按比较结果升序保存键`



## HashMap 和 HashTable的区别

HashMap和HashTable都实现了Map接口，但决定用哪一个之前先要弄清楚它们之间的分别。主要的区别有：`线程安全性`，`同步(synchronization)`，以及`速度`。

1. `HashMap`可以接受为`null`的键值(key)和值(value)，而`HashTable`则不行
2. `HashMap`是非`synchronized`,但是有`CurrentHashMap`是同步的，用来替代`HashTable`
3. HashMap不能保证随着时间的推移Map中的`元素次序是不变的`。
4. 迭代器的区别

## LinkedList 方法的介绍

允许所有元素（`包括 null`)

|retur type |method|
|:----------|:-----|
|boolean|offer(E e)将指定元素添加到此列表的末尾（最后一个元素）。|
| boolean   | offerFirst(E e) 在此列表的开头插入指定的元素。
| boolean    |offerLast(E e) 在此列表末尾插入指定的元素。|
| E | peek()获取但不移除此列表的头（第一个元素）。|
| E  |peekFirst() 获取但不移除此列表的第一个元素；如果此列表为空，则返回 null。|
| E  |peekLast() 获取但不移除此列表的最后一个元素；如果此列表为空，则返回 null。|
| E | poll() 获取并移除此列表的头（第一个元素）|
| E  |pollFirst() 获取并移除此列表的第一个元素；如果此列表为空，则返回 null。|
| E | pollLast() 获取并移除此列表的最后一个元素；如果此列表为空，则返回 null。|
|E  |pop() 从此列表所表示的堆栈处弹出一个元素。|
|void  | push(E e) 将元素推入此列表所表示的堆栈。|
{:.mbtablestyle}
