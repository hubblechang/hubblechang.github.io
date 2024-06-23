---
title: Java基础
categories: 
- Java
---

# Java语法
1. 反射的使用场景：动态代理+注解
反射的实质是程序在运行时检查运行时类加载过程中保存在运行时常量池中的信息。
在运行时分析类以及执行类中方法的能力，通过反射可以获取任意一个类的所有属性和方法，还可以调用这些方法和属性。
```Java
Class alunbarClass = TargetObject.class;

Class alunbarClass1 = Class.forName("cn.javaguide.TargetObject");

TargetObject o = new TargetObject();
Class alunbarClass2 = o.getClass();

ClassLoader.getSystemClassLoader().loadClass("cn.javaguide.TargetObject");  // 通过类加载器获取 Class 对象不会进行初始化，意味着不进行包括初始化等一系列步骤，静态代码块和静态对象不会得到执行
```

2. 泛型的使用方式
泛型类、泛型接口、泛型方法

# Java集合
Java 集合，也叫作容器，主要是由两大接口派生而来：
+ Collection 接口，主要用于存放单一元素；
+ Map 接口，主要用于存放键值对。对于Collection 接口，下面又有三个主要的子接口：List、Set 、Queue。
1. List：
    + ArrayList：Object[] 数组。原始长度为10，每次添加元素前检查空间够不够，扩容规则为`newCapacity = oldCapacity + (oldCapacity >> 1)`
    + Vector：Object[] 数组。
    + LinkedList：双向链表。
2. Set
    + HashSet(无序，唯一): 基于 HashMap 实现的，底层采用 HashMap 来保存元素。
    + LinkedHashSet: LinkedHashSet 是 HashSet 的子类，并且其内部是通过 LinkedHashMap 来实现的。
    + TreeSet(有序，唯一): 红黑树(自平衡的排序二叉树)。
3. Queue
    + PriorityQueue: Object[] 数组来实现小顶堆。
    + DelayQueue:PriorityQueue。
    + ArrayDeque: 可扩容动态双向数组。
4. Map
    + HashMap：<b>Node数组+链表+红黑树</b>。JDK1.8 之前 HashMap 由数组+链表组成的，数组是 HashMap 的主体，链表则是主要为了解决哈希冲突而存在的（“拉链法”解决冲突）。JDK1.8 以后在解决哈希冲突时有了较大的变化，<b>当链表长度大于阈值（默认为 8）（将链表转换成红黑树前会判断，如果当前数组的长度小于 64，那么会选择先进行数组扩容，而不是转换为红黑树）时，将链表转化为红黑树</b>，以减少搜索时间。详细可以查看：HashMap 源码分析。<b>初始化大小为 16。之后每次扩充，容量变为原来的 2 倍。</b>如果给定了容量初始值，先扩充到2的幂次在初始化。
    + LinkedHashMap：LinkedHashMap 继承自 HashMap，所以它的底层仍然是<b>基于拉链式散列结构即由数组和链表或红黑树组成</b>。另外，LinkedHashMap 在上面结构的基础上，增加了一条双向链表，使得上面的结构可以保持键值对的插入顺序。同时通过对链表进行相应的操作，实现了访问顺序相关逻辑。详细可以查看：LinkedHashMap 源码分析
    + Hashtable：<b>数组+链表</b>组成的，数组是 Hashtable 的主体，链表则是主要为了解决哈希冲突而存在的。<b>初始大小为 11，之后每次扩充，容量变为原来的 2n+1。</b>如果给定了容量初始值直接使用。
    + TreeMap：红黑树（自平衡的排序二叉树）。

了解---红黑树的规则：
1. 每个结点或红或黑
2. 根结点是黑色
3. 空叶子结点是黑色
4. 如果一个结点是红色，那么它的子节点是黑色
5. 从任意一个结点出发到空的叶子结点经过的黑结点个数相同