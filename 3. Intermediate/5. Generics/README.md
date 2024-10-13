
# Generics in Kotlin

## Introduction

Generics are a powerful feature in Kotlin that allows you to write flexible and reusable code. With generics, you can create classes, interfaces, and functions that operate on a type parameter, which enables you to define algorithms and data structures that can work with any type while maintaining type safety.

## Why Use Generics?

Generics provide several benefits:

- **Type Safety**: Generics enable compile-time type checking, which helps catch errors early in development.
- **Code Reusability**: You can write a single method or class that can work with different types without needing to overload or rewrite the same code.
- **Elimination of Casting**: When using generics, you don't need to cast types, which reduces runtime errors.

## Generic Classes

You can define a generic class by specifying type parameters in angle brackets (`<>`):

```kotlin
// File: Box.kt
class Box<T>(var item: T) {
    fun getItem(): T {
        return item
    }

    fun setItem(value: T) {
        item = value
    }
}
```

### Using Generic Classes

You can create instances of generic classes with specific types:

```kotlin
// File: Main.kt
fun main() {
    val intBox = Box<Int>(123)
    println("Integer Box: ${intBox.getItem()}") // Output: Integer Box: 123

    val stringBox = Box<String>("Hello Generics")
    println("String Box: ${stringBox.getItem()}") // Output: String Box: Hello Generics
}
```

## Generic Functions

You can also define generic functions:

```kotlin
// File: Main.kt
fun <T> printValue(value: T) {
    println("Value: $value")
}

fun main() {
    printValue(42)            // Output: Value: 42
    printValue("Kotlin")     // Output: Value: Kotlin
    printValue(3.14)         // Output: Value: 3.14
}
```

## Multiple Type Parameters

You can define multiple type parameters for a class or function:

```kotlin
// File: Pair.kt
class Pair<K, V>(var key: K, var value: V) {
    fun getKey(): K = key
    fun getValue(): V = value
}

// File: Main.kt
fun main() {
    val pair = Pair("Kotlin", 1)
    println("Key: ${pair.getKey()}, Value: ${pair.getValue()}") // Output: Key: Kotlin, Value: 1
}
```

## Constraints on Type Parameters

You can impose constraints on type parameters using the `where` clause or using `:` to specify a superclass or interface:

```kotlin
// File: ComparableBox.kt
class ComparableBox<T: Comparable<T>>(var item: T) {
    fun isGreaterThan(other: T): Boolean {
        return item > other
    }
}

// File: Main.kt
fun main() {
    val intBox = ComparableBox(10)
    println(intBox.isGreaterThan(5)) // Output: true

    // The following will not compile because String is not a Comparable<Int>
    // val stringBox = ComparableBox<String>("Kotlin")
}
```

## Generics with Collections

Generics are commonly used with Kotlin collections:

```kotlin
// File: Main.kt
fun main() {
    val list: List<String> = listOf("Apple", "Banana", "Cherry")
    for (item in list) {
        println(item)
    }

    val map: Map<Int, String> = mapOf(1 to "One", 2 to "Two", 3 to "Three")
    for ((key, value) in map) {
        println("Key: $key, Value: $value")
    }
}
```

## Reified Type Parameters

In inline functions, you can use reified type parameters to get type information at runtime:

```kotlin
// File: Main.kt
inline fun <reified T> printType(value: T) {
    println("Value: $value, Type: ${T::class.simpleName}")
}

fun main() {
    printType(42)            // Output: Value: 42, Type: Int
    printType("Kotlin")     // Output: Value: Kotlin, Type: String
}
```

## Conclusion

Generics in Kotlin allow you to create type-safe and reusable code. By using generic classes, functions, and constraints, you can write flexible algorithms and data structures that work with any type. Understanding and utilizing generics will enhance your Kotlin programming skills and lead to more robust applications.
