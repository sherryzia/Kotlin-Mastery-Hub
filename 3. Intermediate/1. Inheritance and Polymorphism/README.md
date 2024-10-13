
# Inheritance and Polymorphism in Kotlin

Inheritance and polymorphism are two fundamental concepts in object-oriented programming (OOP) that allow for code reuse and the creation of flexible software designs. This document will cover both concepts in detail, including practical examples to illustrate their use in Kotlin.

## Table of Contents

1. [What is Inheritance?](#what-is-inheritance)
2. [Types of Inheritance](#types-of-inheritance)
3. [The `open` Keyword](#the-open-keyword)
4. [Overriding Methods](#overriding-methods)
5. [Polymorphism](#polymorphism)
6. [Method Overloading vs. Method Overriding](#method-overloading-vs-method-overriding)
7. [Abstract Classes and Interfaces](#abstract-classes-and-interfaces)
8. [Use Cases and Best Practices](#use-cases-and-best-practices)
9. [Conclusion](#conclusion)

## What is Inheritance?

Inheritance is a mechanism in OOP that allows one class (the child or subclass) to inherit the properties and methods of another class (the parent or superclass). This promotes code reuse and establishes a hierarchical relationship between classes.

### Example of Inheritance

```kotlin
// Parent class
open class Animal {
    open fun sound() {
        println("Animal makes a sound")
    }
}

// Child class
class Dog : Animal() {
    override fun sound() {
        println("Dog barks")
    }
}

fun main() {
    val animal: Animal = Dog()
    animal.sound()  // Output: Dog barks
}
```

In this example, `Dog` inherits from `Animal` and overrides the `sound` method.

## Types of Inheritance

1. **Single Inheritance**: A class inherits from one superclass.
2. **Multilevel Inheritance**: A class inherits from a superclass, and that superclass can also inherit from another class.
3. **Hierarchical Inheritance**: Multiple classes inherit from a single superclass.
4. **Multiple Inheritance**: Not directly supported in Kotlin. However, you can achieve similar behavior using interfaces.

### Example of Multilevel Inheritance

```kotlin
open class Animal {
    open fun sound() {
        println("Animal makes a sound")
    }
}

open class Dog : Animal() {
    override fun sound() {
        println("Dog barks")
    }
}

class Puppy : Dog() {
    override fun sound() {
        println("Puppy whines")
    }
}

fun main() {
    val puppy: Puppy = Puppy()
    puppy.sound()  // Output: Puppy whines
}
```

## The `open` Keyword

In Kotlin, all classes are final by default, meaning they cannot be inherited. To allow a class to be subclassed, you must mark it with the `open` keyword. Similarly, to allow a method to be overridden, you must also use the `open` keyword.

### Example

```kotlin
open class Base {
    open fun display() {
        println("Base class")
    }
}

class Derived : Base() {
    override fun display() {
        println("Derived class")
    }
}
```

## Overriding Methods

When a subclass wants to provide a specific implementation of a method defined in its superclass, it can override that method using the `override` keyword.

### Example

```kotlin
open class Vehicle {
    open fun start() {
        println("Vehicle is starting")
    }
}

class Car : Vehicle() {
    override fun start() {
        println("Car is starting")
    }
}
```

## Polymorphism

Polymorphism is the ability for different classes to be treated as instances of the same class through inheritance. The most common use of polymorphism is when a parent class reference is used to refer to a child class object.

### Example

```kotlin
fun makeSound(animal: Animal) {
    animal.sound()  // Will call the overridden method in the child class
}

fun main() {
    val myDog: Animal = Dog()
    makeSound(myDog)  // Output: Dog barks
}
```

## Method Overloading vs. Method Overriding

- **Method Overloading**: Occurs when two or more methods in the same class have the same name but different parameters.
- **Method Overriding**: Occurs when a subclass provides a specific implementation of a method that is already defined in its superclass.

### Example of Method Overloading

```kotlin
fun add(a: Int, b: Int): Int {
    return a + b
}

fun add(a: Double, b: Double): Double {
    return a + b
}
```

### Example of Method Overriding

```kotlin
open class Animal {
    open fun sound() {
        println("Animal makes a sound")
    }
}

class Cat : Animal() {
    override fun sound() {
        println("Cat meows")
    }
}
```

## Abstract Classes and Interfaces

### Abstract Classes

An abstract class is a class that cannot be instantiated and can contain abstract methods (methods without a body). Subclasses must provide implementations for these methods.

```kotlin
abstract class Shape {
    abstract fun area(): Double
}

class Circle(val radius: Double) : Shape() {
    override fun area(): Double {
        return Math.PI * radius * radius
    }
}
```

### Interfaces

An interface in Kotlin defines a contract that implementing classes must follow. Interfaces can contain abstract methods as well as method implementations.

```kotlin
interface Movable {
    fun move()
}

class Car : Movable {
    override fun move() {
        println("Car is moving")
    }
}
```

## Use Cases and Best Practices

- Use inheritance to promote code reuse and establish a logical hierarchy between classes.
- Prefer composition over inheritance when possible to achieve better flexibility and maintainability.
- Use abstract classes when you want to provide a common base with shared implementation but prevent instantiation.
- Use interfaces to define contracts and allow multiple implementations.

## Conclusion

Inheritance and polymorphism are powerful concepts in Kotlin that enable you to create flexible and reusable code. By leveraging these principles, you can design applications that are easier to maintain and extend. Understanding these concepts is crucial for becoming proficient in Kotlin and object-oriented programming as a whole.
