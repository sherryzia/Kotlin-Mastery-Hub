# Classes and Objects in Kotlin

Kotlin is an object-oriented programming language, and classes are a fundamental concept in Kotlin that allow you to create complex data types. In this section, we will cover:

1. **Defining Classes**
2. **Properties**
3. **Constructors**
4. **Inheritance**
5. **Access Modifiers**
6. **Data Classes**
7. **Companion Objects**
8. **Nested and Inner Classes**
9. **Reflection**

## 1. Defining Classes

A class is defined using the `class` keyword followed by the class name and a block of code that defines its properties and methods.

### Basic Class Definition

```kotlin
// File: BasicClass.kt

class Person {
    // Properties
    var name: String = ""
    var age: Int = 0

    // Method
    fun introduce() {
        println("My name is $name and I am $age years old.")
    }
}

fun main() {
    val person = Person() // Creating an object of the class
    person.name = "Alice"
    person.age = 30
    person.introduce() // Output: My name is Alice and I am 30 years old.
}
```

## 2. Properties

Properties in Kotlin are variables that are defined within a class. They can have getters and setters.

### Properties with Getters and Setters

```kotlin
// File: Properties.kt

class Rectangle(private var width: Double, private var height: Double) {
    // Custom getter
    val area: Double
        get() = width * height

    // Custom setter
    var isSquare: Boolean = width == height
        private set
}

fun main() {
    val rectangle = Rectangle(4.0, 5.0)
    println("Area: ${rectangle.area}") // Output: Area: 20.0
}
```

## 3. Constructors

Kotlin classes can have primary and secondary constructors. The primary constructor is part of the class header, while secondary constructors are defined within the class body.

### Primary Constructor

```kotlin
// File: PrimaryConstructor.kt

class Car(val model: String, val year: Int) {
    fun displayInfo() {
        println("Car model: $model, Year: $year")
    }
}

fun main() {
    val car = Car("Toyota", 2022)
    car.displayInfo() // Output: Car model: Toyota, Year: 2022
}
```

### Secondary Constructor

```kotlin
// File: SecondaryConstructor.kt

class Book(val title: String) {
    var author: String = ""

    // Secondary constructor
    constructor(title: String, author: String) : this(title) {
        this.author = author
    }

    fun displayInfo() {
        println("Book title: $title, Author: $author")
    }
}

fun main() {
    val book = Book("Kotlin Programming", "John Doe")
    book.displayInfo() // Output: Book title: Kotlin Programming, Author: John Doe
}
```

## 4. Inheritance

Kotlin supports inheritance, allowing a class to inherit properties and methods from another class. You can use the `open` keyword to make a class inheritable.

### Inheritance Example

```kotlin
// File: Inheritance.kt

open class Animal(val name: String) {
    open fun makeSound() {
        println("Animal sound")
    }
}

class Dog(name: String) : Animal(name) {
    override fun makeSound() {
        println("Bark!")
    }
}

fun main() {
    val dog = Dog("Buddy")
    dog.makeSound() // Output: Bark!
}
```

## 5. Access Modifiers

Kotlin provides access modifiers to control the visibility of classes, methods, and properties. The main access modifiers are `public`, `private`, `protected`, and `internal`.

### Example of Access Modifiers

```kotlin
// File: AccessModifiers.kt

class Sample {
    private var privateProperty: String = "Private"
    protected open var protectedProperty: String = "Protected"
    internal var internalProperty: String = "Internal"
    var publicProperty: String = "Public"
}

class SubSample : Sample() {
    override var protectedProperty: String = "Overridden Protected"
}

fun main() {
    val sample = Sample()
    // println(sample.privateProperty) // Error: Cannot access 'privateProperty': it is private in 'Sample'
    // println(sample.protectedProperty) // Error: Cannot access 'protectedProperty': it is protected in 'Sample'
    println(sample.internalProperty) // Output: Internal
    println(sample.publicProperty) // Output: Public
}
```

## 6. Data Classes

Data classes are a special type of class in Kotlin primarily used to hold data. They automatically provide `equals()`, `hashCode()`, and `toString()` methods.

### Data Class Example

```kotlin
// File: DataClass.kt

data class User(val name: String, val age: Int)

fun main() {
    val user1 = User("Alice", 25)
    val user2 = User("Alice", 25)

    println(user1) // Output: User(name=Alice, age=25)
    println(user1 == user2) // Output: true (compares the contents)
}
```

## 7. Companion Objects

Companion objects allow you to define static members in a class. You can access them without creating an instance of the class.

### Companion Object Example

```kotlin
// File: CompanionObject.kt

class MathUtils {
    companion object {
        fun add(x: Int, y: Int): Int {
            return x + y
        }
    }
}

fun main() {
    val result = MathUtils.add(5, 3)
    println("Sum: $result") // Output: Sum: 8
}
```

## 8. Nested and Inner Classes

Kotlin allows you to define classes within other classes. A nested class does not hold a reference to the outer class, while an inner class does.

### Nested Class Example

```kotlin
// File: NestedClass.kt

class Outer {
    class Nested {
        fun display() {
            println("Inside Nested Class")
        }
    }
}

fun main() {
    val nested = Outer.Nested()
    nested.display() // Output: Inside Nested Class
}
```

### Inner Class Example

```kotlin
// File: InnerClass.kt

class Outer {
    private val outerProperty = "Outer Property"

    inner class Inner {
        fun display() {
            println("Accessing: $outerProperty")
        }
    }
}

fun main() {
    val inner = Outer().Inner()
    inner.display() // Output: Accessing: Outer Property
}
```

## 9. Reflection

Reflection is a powerful feature in Kotlin that allows you to inspect and interact with classes, methods, and properties at runtime. It can be useful for various scenarios, such as serialization, dependency injection, and more.

### Using Reflection

To use reflection, you typically work with the `KClass` class, which represents a Kotlin class. You can obtain the `KClass` instance of a class using the `::class` syntax.

### Example of Reflection

```kotlin
// File: Reflection.kt

import kotlin.reflect.full.memberProperties

data class Person(val name: String, val age: Int)

fun main() {
    val person = Person("Alice", 30)
    val kClass = person::class

    println("Class Name: ${kClass.simpleName}") // Output: Class Name: Person
    println("Properties:")
    for (property in kClass.memberProperties) {
        println("${property.name}: ${property.get(person)}")
    }
    // Output:
    // Properties:
    // name: Alice
    // age: 30
}
```

### Reflection for Annotations

Reflection can also be used to read annotations at runtime. 

### Example of Annotations with Reflection

```kotlin
// File: AnnotationReflection.kt

@Target(AnnotationTarget.CLASS)
@Retention(AnnotationRetention.RUNTIME)
annotation class JsonSerializable(val tableName: String)

@JsonSerializable("persons")
data class Person(val name: String, val age: Int)

fun main() {
    val kClass = Person::class
    val annotation = kClass.annotations.find { it is JsonSerializable } as? JsonSerializable
    println("Table Name: ${annotation?.tableName}") // Output: Table Name: persons
}
```

## Conclusion

Classes and objects are fundamental concepts in Kotlin that enable you to create and manage complex data structures. Understanding how to define classes, use properties and constructors, implement inheritance, and work with access modifiers is essential for building robust applications. Additionally, leveraging data classes and companion objects can help streamline your code, while nested and inner classes provide additional organization and functionality.

Reflection adds a powerful layer of dynamism, allowing for runtime inspection and manipulation of classes, which can be leveraged for various advanced programming techniques.
