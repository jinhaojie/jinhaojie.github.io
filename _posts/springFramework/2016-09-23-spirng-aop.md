---
layout: post
title: spring之aop
description: spring框架aop的理解
keywords: aop
category : spring framework
tags : [aop , spring]
---
#### AOP的概念
>Aop(Aspect oriented programming): 面向切面编程。与面向对象（
oop）把事物当做一个对象来处理不同的是，Aop将事物当做一些服务所依赖的`公有的属性`，比如`权限验证，事物管理，记录日志等`，就好比一个切面，涵盖了不同对象服务的一些共同点，如下图。

![aop1](/assets/images/aop1.png)

![aop2](/assets/images/aop2.png)

#### AOP的一些专业术语
>
|名称 |解释|
|------------|----|
|切面(Aspect):|在spring中切面表现为一个类，这个类中定义了一系列的要横切到目标对象的操作。|
|通知(Advice)|切面中定义的要横切到目标类的一个具体操作。通知可以分为前置通知(before)，后置通知(after)，环绕通知(around)。| 
|连接点(Join point)|目标对象执行期间允许切面通知切入的点，在spring aop中连接点只能是在方法执行时。|
|切入点(Pointcut)|连接点的匹配模式，切入点通过表达式来指定将切面通知具体切入到哪个目标对象的哪个方法上。 |
|目标对象(Target)|切面通知切入的某个具体对象，spring aop是通过运行时代理来实现的，因此目标对象总是一个代理对象。 |
|织入(Weaving)|切面通知切入到某个具体对象的过程，这个过程可以在编译时完成(使用aspectj编译器可以实现)，也可以在类加载时完成，也可能在运行时完成。在spring aop中只能是在运行时完成。| 
|引入(Introduction)|为已有类动态的添加一些属性或方法。 |


#### AOP实现
```
Spring AOP代理实现有两种:
1. JDK动态代理
2. Cglib框架动态代理 
```
#### AOP小结

> 小结：
* #### Spring AOP的底层通过JDK/cglib动态代理为目标对象进行横向织入:
    1. 若目标对象实现了接口,则Spring使用JDK的java.lang.reflect.Proxy代理.
    2. 若目标对象没有实现接口,则Spring使用cglib库生成目标对象的子类.
* #### Spring只支持方法连接点,不提供属性连接.
* #### 标记为final的方法不能被代理,因为无法进行覆盖.
* #### 程序应优先对针对接口代理,这样便于程序解耦/维护.
