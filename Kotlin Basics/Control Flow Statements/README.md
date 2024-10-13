
# Control Flow in Kotlin

Control flow statements in Kotlin dictate the order in which the statements are executed, allowing you to control the flow of execution in your applications. In this section, we will explore:

1. **Conditional Statements**
   - If Expression
   - When Expression
2. **Loops**
   - For Loop
   - While Loop
   - Do-While Loop

## 1. Conditional Statements

### If Expression

The `if` expression evaluates a condition and executes the corresponding block of code. It can also return a value, making it a more versatile option than in some other programming languages.

#### Basic Usage

```kotlin
// File: IfExpression.kt

fun main() {
    val number = 10

    // Basic if statement
    if (number > 0) {
        println("$number is positive.")
    } else if (number < 0) {
        println("$number is negative.")
    } else {
        println("$number is zero.")
    }
}
```

#### Using `if` as an Expression

You can use `if` as an expression to assign values directly.

```kotlin
// File: IfAsExpression.kt

fun main() {
    val number = -5
    val message = if (number > 0) {
        "$number is positive."
    } else {
        "$number is negative or zero."
    }
    println(message)
}
```

#### Nested If Expressions

You can nest `if` expressions within one another to handle more complex conditions.

```kotlin
// File: NestedIfExpression.kt

fun main() {
    val score = 85

    val grade = if (score >= 90) {
        "A"
    } else if (score >= 80) {
        "B"
    } else if (score >= 70) {
        "C"
    } else {
        "D"
    }

    println("Grade: $grade")
}
```

### When Expression

The `when` expression is a powerful alternative to the `if` statement, especially for handling multiple conditions.

#### Basic Usage

```kotlin
// File: WhenExpression.kt

fun main() {
    val day = 4
    val dayName = when (day) {
        1 -> "Monday"
        2 -> "Tuesday"
        3 -> "Wednesday"
        4 -> "Thursday"
        5 -> "Friday"
        6 -> "Saturday"
        7 -> "Sunday"
        else -> "Invalid day"
    }

    println("The day is: $dayName")
}
```

#### Using `when` Without an Argument

You can use `when` without an argument to evaluate conditions.

```kotlin
// File: WhenWithoutArgument.kt

fun main() {
    val number = 15

    when {
        number < 0 -> println("$number is negative")
        number in 1..10 -> println("$number is between 1 and 10")
        else -> println("$number is greater than 10")
    }
}
```

#### Using `when` as an Expression

Like `if`, `when` can also return a value.

```kotlin
// File: WhenAsExpression.kt

fun main() {
    val number = 4
    val message = when (number) {
        1 -> "One"
        2 -> "Two"
        3 -> "Three"
        4 -> "Four"
        else -> "Unknown"
    }

    println(message)
}
```

#### Checking Types

`when` can also be used to check types in a more elegant way.

```kotlin
// File: WhenTypeCheck.kt

fun main() {
    val obj: Any = "Hello"

    when (obj) {
        is String -> println("It's a String of length ${obj.length}")
        is Int -> println("It's an Integer")
        else -> println("Unknown type")
    }
}
```

## 2. Loops

Loops allow you to execute a block of code multiple times, which is essential for performing repetitive tasks.

### For Loop

The `for` loop in Kotlin iterates over a range, array, or collection.

#### Basic Usage

```kotlin
// File: ForLoop.kt

fun main() {
    // Using a range
    for (i in 1..5) {
        println("Iteration: $i")
    }
}
```

#### Iterating Over Collections

You can iterate over collections, such as lists and arrays.

```kotlin
// File: ForLoopCollections.kt

fun main() {
    val fruits = listOf("Apple", "Banana", "Cherry")

    for (fruit in fruits) {
        println("Fruit: $fruit")
    }
}
```

#### Using Indices

If you need the index of each item while iterating, you can use the `indices` property.

```kotlin
// File: ForLoopWithIndex.kt

fun main() {
    val fruits = listOf("Apple", "Banana", "Cherry")

    for (index in fruits.indices) {
        println("Index: $index, Fruit: ${fruits[index]}")
    }
}
```

#### Step and DownTo

You can use `step` to skip elements or `downTo` to count downwards.

```kotlin
// File: ForLoopStep.kt

fun main() {
    // Loop with step
    for (i in 1..10 step 2) {
        println("Step: $i") // Prints 1, 3, 5, 7, 9
    }
}

// File: ForLoopDownTo.kt

fun main() {
    // Counting downwards
    for (i in 5 downTo 1) {
        println("Countdown: $i") // Prints 5, 4, 3, 2, 1
    }
}
```

### While Loop

The `while` loop continues executing as long as the specified condition is true.

#### Basic Usage

```kotlin
// File: WhileLoop.kt

fun main() {
    var count = 1

    while (count <= 5) {
        println("Count: $count")
        count++
    }
}
```

#### Infinite Loop Example

Be careful with the while loop; if the condition never becomes false, it creates an infinite loop.

```kotlin
// File: InfiniteWhileLoop.kt

fun main() {
    var count = 1

    while (true) {
        println("Count: $count")
        count++

        // Break the loop at a certain condition
        if (count > 5) break
    }
}
```

### Do-While Loop

The `do-while` loop executes the block of code at least once before checking the condition.

#### Basic Usage

```kotlin
// File: DoWhileLoop.kt

fun main() {
    var count = 1

    do {
        println("Count: $count")
        count++
    } while (count <= 5)
}
```

### Break and Continue Statements

#### Break Statement

The `break` statement terminates the loop and transfers control to the statement immediately following the loop.

```kotlin
// File: BreakStatement.kt

fun main() {
    for (i in 1..10) {
        if (i == 5) break // Exit loop when i is 5
        println("Current Number: $i")
    }
}
```

#### Continue Statement

The `continue` statement skips the current iteration and continues with the next iteration of the loop.

```kotlin
// File: ContinueStatement.kt

fun main() {
    for (i in 1..10) {
        if (i % 2 == 0) continue // Skip even numbers
        println("Odd Number: $i")
    }
}
```

## Conclusion

Control flow statements are essential for managing how your program operates. They allow for decision-making, looping through collections, and iterating over ranges, which are fundamental concepts in programming. Understanding the different usages of `if`, `when`, `for`, `while`, and `do-while` statements will help you create more complex and dynamic Kotlin applications.

By mastering these control flow constructs, you will enhance your Kotlin programming skills significantly, making your code more efficient and readable.
