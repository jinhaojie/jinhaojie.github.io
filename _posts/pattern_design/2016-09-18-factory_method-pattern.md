---
layout: post
title: 设计模式之--简单工厂模式
description: pattern design
keywords: pattern design
category : 设计模式
tags : [pattern design , 设计模式]
---
#### 简述
　　按照《java与模式》,工厂模式可以细分为`简单工厂模式`, `工厂方法模式`　和`抽象工厂模式`。　本文主要讨论的是`简单工厂`模式。简单工厂模式是对某一类产品的生产。一般用于具体产品很少扩展的项目。


#### 长篇大论不如先来一张图
![factory](/assets/images/pattern_design/simple_factory-pattern.png)

>　在上面的图中，描述了一个通用的方案，通过用一个汽车工厂来构造3种类型的汽车：small,sedan和luxury。这是一种松耦合的的设计模式，它将具体汽车的实现隐藏起来，对客户端只展示了一个通用的接口。

#### 下面我们来看看代码的实现

{%highlight  java linenos%}
//抽象产品  
abstract class Car{  
    private String name;  
      
    public abstract void drive();  
      
    public String getName() {  
        return name;  
    }  
    public void setName(String name) {  
        this.name = name;  
    }  
}  
//具体产品  
class Benz extends Car{  
    public void drive(){  
        System.out.println(this.getName()+"----go-----------------------");  
    }  
}  
class Bmw extends Car{  
    public void drive(){  
        System.out.println(this.getName()+"----go-----------------------");  
    }  
}  
  
  
//抽象工厂  
abstract class Factory{  
    public abstract Car createCar(String car) throws Exception;  
}  
//具体工厂（每个具体工厂负责一个具体产品）  
class BenzFactory extends Driver{  
    public Car createCar(String car) throws Exception {  
        return new Benz();  
    }  
}  
class BmwFactory extends Driver{  
    public Car createCar(String car) throws Exception {  
        return new Bmw();  
    }  
}  
  
//测试  
public class Boss{  
  
    public static void main(String[] args) throws Exception {  
        Factory d = new BenzFactory();  
        Car c = d.createCar("benz");   
        c.setName("benz");  
        c.drive();  
    }  
}  

{%endhighlight%}

说明：　当我们需要某个产品时，就去得到一个具体的工厂实例，然后用这个工厂实例去生产我们需要的产品

#### 下面总结一下工厂方法的优点和缺点


>优点
    1.完全符合开闭原则，在扩展某类产品时候，不需要去修改抽象工厂，只需要添加新的工厂类，和新的产品类，而不需要修改任何原有的类或方法。
    ２.具有良好的扩展性
    
   

>缺点
    如果产品种类很多，势必有很多具体的工厂类。
