# Notes on Kotlin 

## Variables

- Mutable: `var`
- Immutable: `val`

## Condition

```kt
when (cond) {
    null -> 1
    else -> 2
}
```

## Functions

- Basic function

```kt
fun sayHi(): String {
    return "Hi"
}
```

- Nullable string

```kt
fun sayHi(): String? {
    return "Hi"
}
```

- Unit type can be ommited

```kt
fun main(): Unit {
    println("Hello World")
}
```

- Single expression function

```kt
fun sayHi(): String = "Hi"
```

- Function parameters

```kt
fun saySmth(smth1: String, smth2: String) {
    val msg = "$smth1 $smth2"
    println(msg)
}
```

## Collections

- Array

```kt
val langs = arrayOf("kotlin", "java", "go")
```

- List

```kt
val langs = listOf("kotlin", "java", "go")
```

- Map

```kt
val langs = mapOf(1 to "kotlin", 2 to "java", 3 to "go")
```

- Loop

```kt
for (lang in langs) {
    println(lang)
}
```

- Loop using lambda syntax

```kt
langs.forEach { lang ->
    println(lang)
}
```

- Loop using lambda syntax with index

```kt
langs.forEach {index, lang -> 
    println("$lang is at index $index")
}
```

{% hint style=info %}
By default collection type is immutable. Use `mutable...Of()` to make it mutable
{% endhint %}


## vararg
