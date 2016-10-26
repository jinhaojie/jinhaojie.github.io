---
layout: post
title: 设计模式之--工厂方法模式
description: pattern design
keywords: pattern design
category : 设计模式
tags : [pattern design , 设计模式]
---
#### 简述
　　按照《java与模式》,工厂模式可以细分为`简单工厂模式`, `工厂方法模式`　和`抽象工厂模式`。　本文主要讨论的是`工厂方法`模式。工厂方法模式针对的是便于扩展产品种类的项目，对于每一类的产品都对应一个具体的工厂类。


#### 长篇大论不如先来一张图
![factory](/assets/images/pattern_design/factory_method-pattern.png)

>　在上面的图中，对每一类产品，都有一个具体的工厂类去生产。
#### 下面我们来看看代码的实现

**Cartype.java**  一个枚举类，存储汽车的类型 

{%highlight  java linenos%}
package designPatterns.creational.factory;
 
public enum CarType {
    SMALL, SEDAN, LUXURY
}
{%endhighlight%}

**Car.java** 所有汽车接口的父类，包含了通用的制造汽车的接口

{%highlight  java linenos%}
 
public interface  Car {
 
    public Car(CarType model) {
        this.model = model;
        arrangeParts();
    }
 
    private void arrangeParts() {
        // Do one time processing here
    }
 
    // Do subclass level processing in this method
    protected abstract void construct();
 
    private CarType model = null;
 
    public CarType getModel() {
        return model;
    }
 
    public void setModel(CarType model) {
        this.model = model;
    }
}
{%endhighlight%}

**LuxuryCar.java** 具体的汽车（Luxury)的实现类。
{%highlight java linenos%}
package designPatterns.creational.factory;
 
public class LuxuryCar extends Car {
 
    LuxuryCar() {
        super(CarType.LUXURY);
        construct();
    }
 
    @Override
    protected void construct() {
        System.out.println("Building luxury car");
        // add accessories
    }
}
{%endhighlight%}

**SmallCar.java**具体的汽车实现类: SMALL
{%highlight java linenos%}
package designPatterns.creational.factory;
 
public class SmallCar extends Car {
 
    SmallCar() {
        super(CarType.SMALL);
        construct();
    }
 
    @Override
    protected void construct() {
        System.out.println("Building small car");
        // add accessories
    }
}
{%endhighlight%}
**SedanCar.java** 具体的汽车实现类: SEDAN
{%highlight java linenos%}
package designPatterns.creational.factory;
 
public class SedanCar extends Car {
 
    SedanCar() {
        super(CarType.SEDAN);
        construct();
    }
 
    @Override
    protected void construct() {
        System.out.println("Building sedan car");
        // add accessories
    }
}
{%endhighlight%}
**CarFactory.java**汽车工厂类，包含了一个实例化一个汽车，只取决于汽车的类型. 

{%highlight java linenos%}
package designPatterns.creational.factory;
 
public class CarFactory {
    public static Car buildCar(CarType model) {
        Car car = null;
        switch (model) {
        case SMALL:
            car = new SmallCar();
            break;
 
        case SEDAN:
            car = new SedanCar();
            break;
 
        case LUXURY:
            car = new LuxuryCar();
            break;
 
        default:
            // throw some exception
            break;
        }
        return car;
    }
}
{%endhighlight%}

**TestFactoryPattern.java** 用来测试Factory类.
{%highlight java linenos%}

package designPatterns.creational.factory;
 
public class TestFactoryPattern {
    public static void main(String[] args) {
        System.out.println(CarFactory.buildCar(CarType.SMALL));
        System.out.println(CarFactory.buildCar(CarType.SEDAN));
        System.out.println(CarFactory.buildCar(CarType.LUXURY));
    }
}
 
Output:
 
Building small car
designPatterns.creational.factory.SmallCar@7c230be4
Building sedan car
designPatterns.creational.factory.SedanCar@60e1e567
Building luxury car
designPatterns.creational.factory.LuxuryCar@e9bfee2
{%endhighlight%}

#### 下面总结一下简单工厂的优点和缺点


>优点
    1. 对象的创建避免了代码的重复
    2. 对象的创建所需要的权限资源不在暴露的类中
    3. 中心化对象创建的声明周期管理，确保在平台中对象能够有一致的表现
    
   

>缺点
    1.  扩展性差。每次增加一个产品时，都需要增加一个具体类和对象实现工厂，是的系统中类的个数成倍增加，在一定程度上增加了系统的复杂度，同时也增加了系统具体类的依赖。这并不是什么好事。
    ２.  在编码上不符合开闭原则（对扩展开放，对修改关闭），没增减一个产品都需要修改原来的工厂。
