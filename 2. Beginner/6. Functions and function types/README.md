
# Functions in Kotlin

Functions are a fundamental building block in Kotlin, allowing you to encapsulate reusable pieces of code. They can take parameters, return values, and help organize code logically. In this section, we will cover:

1. **Defining Functions**
2. **Function Parameters**
3. **Return Values**
4. **Default and Named Arguments**
5. **Variable-Length Arguments (Varargs)**
6. **Higher-Order Functions**
7. **Inline Functions**
8. **Extension Functions**

## 1. Defining Functions

Functions in Kotlin are defined using the `fun` keyword, followed by the function name, parameters (if any), and the return type.

### Basic Function Definition

```kotlin
// File: BasicFunction.kt

fun greet() {
    println("Hello, Kotlin!")
}

fun main() {
    greet() // Calling the function
}
```

## 2. Function Parameters

You can define functions that accept parameters. Each parameter must have a specified type.

### Function with Parameters

```kotlin
// File: FunctionWithParameters.kt

fun greetUser(name: String) {
    println("Hello, $name!")
}

fun main() {
    greetUser("Alice") // Output: Hello, Alice!
}
```

### Multiple Parameters

You can define functions with multiple parameters.

```kotlin
// File: FunctionWithMultipleParameters.kt

fun add(a: Int, b: Int): Int {
    return a + b
}

fun main() {
    val sum = add(5, 3)
    println("Sum: $sum") // Output: Sum: 8
}
```

## 3. Return Values

Functions can return a value using the `return` keyword. The return type is specified after the parameter list.

### Function with Return Value

```kotlin
// File: FunctionWithReturnValue.kt

fun multiply(x: Int, y: Int): Int {
    return x * y
}

fun main() {
    val result = multiply(4, 5)
    println("Result: $result") // Output: Result: 20
}
```

## 4. Default and Named Arguments

Kotlin allows you to provide default values for parameters. This way, you can call the function without passing all arguments.

### Default Arguments

```kotlin
// File: FunctionWithDefaultArguments.kt

fun greet(name: String = "Guest") {
    println("Hello, $name!")
}

fun main() {
    greet() // Output: Hello, Guest!
    greet("Bob") // Output: Hello, Bob!
}
```

### Named Arguments

You can specify arguments by name when calling a function, improving readability.

```kotlin
// File: FunctionWithNamedArguments.kt

fun displayInfo(name: String, age: Int) {
    println("Name: $name, Age: $age")
}

fun main() {
    displayInfo(age = 30, name = "Alice") // Output: Name: Alice, Age: 30
}
```

## 5. Variable-Length Arguments (Varargs)

You can define functions that accept a variable number of arguments using the `vararg` keyword.

### Varargs Example

```kotlin
// File: FunctionWithVarargs.kt

fun printNumbers(vararg numbers: Int) {
    for (number in numbers) {
        println(number)
    }
}

fun main() {
    printNumbers(1, 2, 3, 4, 5) // Prints: 1, 2, 3, 4, 5
}
```

## 6. Higher-Order Functions

Higher-order functions are functions that take other functions as parameters or return them.

### Basic Higher-Order Function

```kotlin
// File: HigherOrderFunction.kt

fun performOperation(a: Int, b: Int, operation: (Int, Int) -> Int): Int {
    return operation(a, b)
}

fun add(x: Int, y: Int): Int {
    return x + y
}

fun main() {
    val result = performOperation(10, 20, ::add)
    println("Result: $result") // Output: Result: 30
}
```

### Lambda Expressions as Higher-Order Functions

You can also use lambda expressions for higher-order functions.

```kotlin
// File: HigherOrderFunctionWithLambda.kt

fun performOperation(a: Int, b: Int, operation: (Int, Int) -> Int): Int {
    return operation(a, b)
}

fun main() {
    val result = performOperation(10, 20) { x, y -> x * y }
    println("Result: $result") // Output: Result: 200
}
```

## 7. Inline Functions

Inline functions are used to reduce the overhead of higher-order functions. They allow the compiler to inline the function’s code at the call site.

### Inline Function Example

```kotlin
// File: InlineFunction.kt

inline fun inlineFunction(block: () -> Unit) {
    println("Before executing the block")
    block() // Calls the lambda function passed
    println("After executing the block")
}

fun main() {
    inlineFunction { println("Inside the block") }
}
// Output:
// Before executing the block
// Inside the block
// After executing the block
```

## 8. Extension Functions

Extension functions allow you to add new functionality to existing classes without modifying their source code.

### Defining an Extension Function

```kotlin
// File: ExtensionFunction.kt

fun String.addExclamation(): String {
    return this + "!"
}

fun main() {
    val message = "Hello, Kotlin"
    println(message.addExclamation()) // Output: Hello, Kotlin!
}
```

## Conclusion

Functions are an essential part of Kotlin programming, allowing you to write clean, reusable, and modular code. By mastering function definitions, parameters, return values, higher-order functions, and extensions, you can significantly enhance your Kotlin development skills. Understanding these concepts will enable you to build more complex applications efficiently.
