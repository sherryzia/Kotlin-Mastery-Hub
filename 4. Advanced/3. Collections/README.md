
# Collections in Kotlin

Kotlin provides a rich set of collection types that allow developers to store and manipulate groups of data. Collections are fundamental to programming, and Kotlin's collections framework is designed to be intuitive, flexible, and powerful.

## Key Concepts

1. **Collections Overview**
   - Collections in Kotlin can be categorized into two main types:
     - **Mutable Collections**: These allow modification (adding, removing, updating elements).
     - **Read-Only Collections**: These are immutable and do not allow modification.
   - Collections can also be classified based on their internal data structure:
     - **Lists**: Ordered collections of elements that can contain duplicates.
     - **Sets**: Unordered collections that do not allow duplicates.
     - **Maps**: Collections of key-value pairs, where each key is unique.

## 1. Lists

Lists are ordered collections that can hold duplicates. Kotlin provides several implementations for lists.

### 1.1. Read-Only List

```kotlin
fun main() {
    val readOnlyList: List<String> = listOf("Apple", "Banana", "Cherry", "Apple")

    println("Read-Only List:")
    println(readOnlyList) // Output: [Apple, Banana, Cherry, Apple]
}
```

### 1.2. Mutable List

Mutable lists allow modifications such as adding, removing, or updating elements.

```kotlin
fun main() {
    val mutableList: MutableList<String> = mutableListOf("Apple", "Banana")
    mutableList.add("Cherry")
    mutableList.remove("Banana")
    
    println("Mutable List:")
    println(mutableList) // Output: [Apple, Cherry]
}
```

### 1.3. List Operations

- **Accessing Elements**: Use indexing to access elements.
- **Iterating**: Use `forEach`, `for` loop, or higher-order functions like `map`.

```kotlin
fun main() {
    val fruits = listOf("Apple", "Banana", "Cherry")

    // Accessing elements
    println("First fruit: ${fruits[0]}") // Output: First fruit: Apple

    // Iterating
    fruits.forEach { fruit -> println(fruit) }
}
```

## 2. Sets

Sets are unordered collections that do not allow duplicate elements. Kotlin provides two types of sets: read-only and mutable.

### 2.1. Read-Only Set

```kotlin
fun main() {
    val readOnlySet: Set<String> = setOf("Apple", "Banana", "Cherry", "Apple")

    println("Read-Only Set:")
    println(readOnlySet) // Output: [Apple, Banana, Cherry]
}
```

### 2.2. Mutable Set

```kotlin
fun main() {
    val mutableSet: MutableSet<String> = mutableSetOf("Apple", "Banana")
    mutableSet.add("Cherry")
    mutableSet.remove("Banana")

    println("Mutable Set:")
    println(mutableSet) // Output: [Apple, Cherry]
}
```

### 2.3. Set Operations

- **Adding and Removing Elements**: Use `add()`, `remove()`, and `contains()`.
- **Iterating**: Similar to lists, you can iterate using `forEach` or `for` loop.

```kotlin
fun main() {
    val fruits = mutableSetOf("Apple", "Banana", "Cherry")

    // Adding elements
    fruits.add("Orange")
    
    // Removing elements
    fruits.remove("Banana")

    // Iterating
    fruits.forEach { fruit -> println(fruit) }
}
```

## 3. Maps

Maps are collections of key-value pairs where each key is unique. Kotlin provides two types of maps: read-only and mutable.

### 3.1. Read-Only Map

```kotlin
fun main() {
    val readOnlyMap: Map<String, Int> = mapOf("Apple" to 1, "Banana" to 2, "Cherry" to 3)

    println("Read-Only Map:")
    println(readOnlyMap) // Output: {Apple=1, Banana=2, Cherry=3}
}
```

### 3.2. Mutable Map

```kotlin
fun main() {
    val mutableMap: MutableMap<String, Int> = mutableMapOf("Apple" to 1, "Banana" to 2)
    mutableMap["Cherry"] = 3
    mutableMap.remove("Banana")

    println("Mutable Map:")
    println(mutableMap) // Output: {Apple=1, Cherry=3}
}
```

### 3.3. Map Operations

- **Accessing Values**: Use the key to access the corresponding value.
- **Iterating**: Use `forEach` or iterate over entries.

```kotlin
fun main() {
    val fruitPrices = mapOf("Apple" to 1, "Banana" to 2, "Cherry" to 3)

    // Accessing a value
    println("Price of Apple: ${fruitPrices["Apple"]}") // Output: Price of Apple: 1

    // Iterating over entries
    fruitPrices.forEach { (fruit, price) -> println("$fruit: $price") }
}
```

## 4. Collection Operations

Kotlin collections provide various built-in functions for common operations, including:

### 4.1. Filtering

```kotlin
fun main() {
    val numbers = listOf(1, 2, 3, 4, 5, 6)
    val evenNumbers = numbers.filter { it % 2 == 0 }

    println("Even Numbers: $evenNumbers") // Output: Even Numbers: [2, 4, 6]
}
```

### 4.2. Mapping

```kotlin
fun main() {
    val numbers = listOf(1, 2, 3, 4)
    val squares = numbers.map { it * it }

    println("Squares: $squares") // Output: Squares: [1, 4, 9, 16]
}
```

### 4.3. Reducing

```kotlin
fun main() {
    val numbers = listOf(1, 2, 3, 4)
    val sum = numbers.reduce { acc, number -> acc + number }

    println("Sum: $sum") // Output: Sum: 10
}
```

### 4.4. Sorting

```kotlin
fun main() {
    val numbers = listOf(3, 1, 4, 2)
    val sortedNumbers = numbers.sorted()

    println("Sorted Numbers: $sortedNumbers") // Output: Sorted Numbers: [1, 2, 3, 4]
}
```

### 4.5. Other Useful Functions

- **`contains()`**: Check if a collection contains a specific element.
- **`size`**: Get the size of a collection.
- **`isEmpty()` / `isNotEmpty()`**: Check if a collection is empty or not.

## 5. Collection Type Aliases

Kotlin allows you to create type aliases for collections to enhance readability. 

### Example of Type Alias

```kotlin
typealias FruitBasket = List<String>

fun main() {
    val basket: FruitBasket = listOf("Apple", "Banana", "Cherry")
    println("Fruit Basket: $basket")
}
```

## 6. Conclusion

Kotlin’s collections framework provides a powerful and expressive way to handle groups of data. With built-in support for lists, sets, and maps, and a rich set of extension functions, Kotlin makes it easy to perform common operations on collections. Understanding collections is essential for effective Kotlin programming and software development in general.

In the next section, we will explore coroutines, a powerful feature in Kotlin for asynchronous programming and concurrency management.
