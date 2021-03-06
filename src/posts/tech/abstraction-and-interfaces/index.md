---
path:  "/tech/abstraction-and-interfaces"
title: Abstraction and interfaces
subtitle: When to use abstraction and when to use interfaces
excerpt: Abstraction and interfaces are common words that most programmers will come across when desigining systems and platforms. They are very useful concepts that any programmer who knows about Object Oriented Programming (OOP) should grasp and know like the back of their hand. They not only make code readable and testable, but also make your life a hell of a lot easier.
tags: [abstraction, interfaces, oop]
category: tech
date: "2016-10-28T12:00:00+00:00"
author:
  name: Brian Lusina
  link: "/brian_lusina"
  avatar: brian_lusina.jpg
image:
 feature: abstract_class_interfaces.png
 teaser: abstract_class_interfaces.png
 thumbnail: abstract_class_interfaces.png
 creditlink: http://agile-code.com
 credit: Agile Code
published: true
---

Abstraction and interfaces are common words that most programmers will come across when desigining systems and platforms. They are very useful concepts that any programmer who knows about Object Oriented Programming (OOP) should grasp and know like the back of their hand. They not only make code readable and testable, but also make your life a hell of a lot easier.

Alright,let us get to it, so, I shall write about abstraction and interface in the Java programming language. However these very concepts can be applied to any OOP language out there.

## Abstract classes

These are classes that contain one or more abstract methods. An abstract method is one that is declared but contains no implementation (without braces and followed by a semi-colon).

```java
abstract void drive(double speed);
```

If a class contains abstract methods then the class **must** be declared abstract. When an abstract class is subclassed, the subclass usually provides implementations for all of the abstract methods in its parent class. However, if it does not, then the subclass must also be declared abstract.

```java
abstract class Car{

	abstract void changeGear(int number);
}
```

Take for example we are modelling animals, we may start the hierachy with a base class of _Animal_. Animals are capable of several things, flying, running, swimming, crawling. They are also capable of sleeping, eating, dreaming. In this regard, the many types of animals have similar characteristics, like eating and sleeping. So the common operations performed by animals, but in a different way is a good candidate for abstraction which will force the subclasses (or child classes) to provide their own implementation. Let us take the following example.

```java
	abstract class Animal {

        /**Types of food the animals eat*/
        public abstract void eat(String food);

        /**How long the anima will sleep*/
        public void sleep(int hours){
            try{
                // 1000 milliseconds * 60 seconds * 60 minutes * hours
                Thread.sleep(1000 * 60 *60 *hours);
            }catch (InterruptedException ie){
                ie.printStackTrace();
            }
        }

        /**The sound the animals make*/
        public abstract void makeNoise();
    }
```

The **abstract** keyword is used in both the class and the method to declare that the class and the method are abstract. Any class that subclasses `Animal` must implement the `makeNoise` and the `eat` functions.

```java
	public class Cat extends Animal{
    	@Override
        public void eat(String food) {
            System.out.println("Cats eat " + food);
        }

        @Override
        public void makeNoise() {
            System.out.println("Cats meow a lot");
        }
	}
```

Alternatively we could declare Animal as an interface instead of using an abstract class, and have the Cat implement the interface. You could - but you'd also need to implement the sleep method. By using abstract classes, you can inherit the implementation of other (non-abstract) methods. You can't do that with interfaces - an interface cannot provide any method implementations.

## Abstract classes and Interfaces

Now, that we have a basic understanding of abstraction, we shal compare that to interfaces. What is the difference? They are similar in a way, but are obviously not the same. You **can't** instantiate an abstract class and they may contain a mix of methods containing a mix of methods declared with or without an implementation. With abstract classes, you can declare fields that are not static and final, and define public, protected, and private concrete methods. With interfaces on the other hand, all fields are automatically public, static, and final, and all methods that you declare or define (as default methods) are public. In addition, you can extend only one class, whether or not it is abstract, whereas you can implement any number of interfaces (basics of OOP).

## Instances to use Abstract classes and Interfaces.

Abstract classes are best used in such scenarios:

- You want to share code among several closely related classes.
- You expect that classes that extend your abstract class have many common methods or fields, or require access modifiers other than public (such as protected and private).
- You want to declare non-static or non-final fields. This enables you to define methods that can access and modify the state of the object to which they belong.

Interfaces on the other hand are best used in such scenarios:

- You expect that unrelated classes would implement your interface.
- You want to specify the behavior of a particular data type, but not concerned about who implements its behavior.
- You want to take advantage of multiple inheritance of type.

These obviously are not the only scenarios, they are just but examples. A real practical example of Abstraction is found [here](https://github.com/BrianLusina/Java-Playground/tree/master/AbstractionInterfaces/MotorVehicles).
