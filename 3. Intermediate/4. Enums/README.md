
# Enums in Kotlin

## Introduction

Enums, short for enumerations, are a special data type in Kotlin that allows you to define a variable that can hold a set of predefined constants. Using enums can help you work with fixed sets of related constants in a type-safe manner. 

## Defining Enums

In Kotlin, you can define an enum class using the `enum` keyword followed by the class name. Each enum constant is defined as a static member of the enum class. Here’s a simple example:

```kotlin
// File: Day.kt
enum class Day {
    SUNDAY, MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY
}
```

### Accessing Enum Constants

You can access enum constants using the enum class name followed by the constant name:

```kotlin
// File: Main.kt
fun main() {
    val today: Day = Day.WEDNESDAY
    println("Today is: $today")
}
```

## Properties and Methods in Enums

Enum classes can also have properties and methods. You can define properties in the constructor of the enum class.

### Example with Properties

```kotlin
// File: Planet.kt
enum class Planet(val mass: Double, val radius: Double) {
    MERCURY(3.303e+20, 2.4397e6),
    VENUS(4.869e+24, 6.0518e6),
    EARTH(5.976e+24, 6.378e6),
    MARS(6.421e+23, 3.3972e6);

    fun surfaceGravity(): Double {
        return G * mass / (radius * radius)
    }

    companion object {
        const val G = 6.673e-11
    }
}
```

### Accessing Properties and Methods

You can access properties and methods of enum constants like this:

```kotlin
// File: Main.kt
fun main() {
    val earth = Planet.EARTH
    println("Surface gravity on Earth: ${earth.surfaceGravity()}")
}
```

## Enum as a Parameter

Enums can also be used as parameters in functions:

```kotlin
// File: Main.kt
fun printDayType(day: Day) {
    when (day) {
        Day.SATURDAY, Day.SUNDAY -> println("It's a weekend!")
        else -> println("It's a weekday.")
    }
}

fun main() {
    printDayType(Day.MONDAY)  // Output: It's a weekday.
    printDayType(Day.SATURDAY) // Output: It's a weekend!
}
```

## Iterating Over Enums

You can iterate over the values of an enum using the `values()` method:

```kotlin
// File: Main.kt
fun main() {
    for (day in Day.values()) {
        println(day)
    }
}
```

## Using Enums in `when` Expressions

Enums are often used with `when` expressions to perform different actions based on the enum value:

```kotlin
// File: Main.kt
fun describe(day: Day): String {
    return when (day) {
        Day.SATURDAY, Day.SUNDAY -> "Weekend"
        else -> "Weekday"
    }
}

fun main() {
    println(describe(Day.FRIDAY)) // Output: Weekday
    println(describe(Day.SATURDAY)) // Output: Weekend
}
```

## Conclusion

Enums in Kotlin provide a powerful way to work with fixed sets of constants in a type-safe manner. They can have properties and methods, and they can be used in various programming constructs like functions and `when` expressions. By using enums, you can improve code readability and maintainability.