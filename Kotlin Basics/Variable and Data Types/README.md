
# Variables and Data Types

In Kotlin, variables are used to store data that can be changed during the execution of a program. Understanding the various data types available in Kotlin is crucial for effective programming.

## Topics Covered

1. **Variable Types**
   - Mutable vs. Immutable variables.
2. **Data Types**
   - Basic data types: Int, Double, Boolean, Char, String.
   - Nullable types.

## 1. Variable Types

### Mutable Variables

Mutable variables can change their value. In Kotlin, you declare a mutable variable using the `var` keyword.

```kotlin
// File: MutableVariables.kt

fun main() {
    var age: Int = 25 // Mutable variable
    println("Age: $age")
    
    age = 26 // Changing the value
    println("Updated Age: $age")
}
```

### Immutable Variables

Immutable variables cannot change their value once assigned. In Kotlin, you declare an immutable variable using the `val` keyword.

```kotlin
// File: ImmutableVariables.kt

fun main() {
    val name: String = "John Doe" // Immutable variable
    println("Name: $name")

    // Uncommenting the line below will cause a compilation error
    // name = "Jane Doe" // Error: Val cannot be reassigned
}
```

## 2. Data Types

Kotlin provides several built-in data types:

### Numeric Types

- **Int**: Represents integer values.
- **Double**: Represents double-precision floating-point values.
- **Float**: Represents single-precision floating-point values.

```kotlin
// File: NumericTypes.kt

fun main() {
    val integerNumber: Int = 42
    val doubleNumber: Double = 3.14
    val floatNumber: Float = 2.71f

    println("Integer: $integerNumber")
    println("Double: $doubleNumber")
    println("Float: $floatNumber")
}
```

### Boolean Type

- **Boolean**: Represents true or false values.

```kotlin
// File: BooleanType.kt

fun main() {
    val isKotlinFun: Boolean = true
    val isFishTasty: Boolean = false

    println("Is Kotlin fun? $isKotlinFun")
    println("Is fish tasty? $isFishTasty")
}
```

### Character Type

- **Char**: Represents a single character.

```kotlin
// File: CharacterType.kt

fun main() {
    val letter: Char = 'A'
    println("Character: $letter")
}
```

### String Type

- **String**: Represents a sequence of characters.

```kotlin
// File: StringType.kt

fun main() {
    val greeting: String = "Hello, Kotlin!"
    println(greeting)
}
```

### Nullable Types

Kotlin distinguishes between nullable and non-nullable types. To define a variable that can hold null, you can use the `?` symbol.

```kotlin
// File: NullableTypes.kt

fun main() {
    var nullableString: String? = null // Nullable variable
    println("Nullable String: $nullableString")

    nullableString = "Now I'm not null"
    println("Updated Nullable String: $nullableString")
}
```

## Conclusion

Understanding variables and data types is fundamental in Kotlin programming. This knowledge allows you to manage and manipulate data effectively in your applications. Experiment with the provided code snippets to deepen your understanding.
