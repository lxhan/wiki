# Notes on Kotlin 

## Variables

- Mutable: `var`
- Immutable: `val`

## Condition

```
when (cond) {
    null -> 1
    else -> 2
}
```

## Functions

- Basic function
```
fun sayHi(): String {
    return "Hi"
}
```

- Nullable string
```
fun sayHi(): String? {
    return "Hi"
}
```

- Unit type can be ommited
```
fun main(): Unit {
    println("Hello World")
}
```

- Single expression function
```
fun sayHi(): String = "Hi"
```

- Function parameters
```
fun sahSmth(smth1: String, smth2: String) {
    val msg = "$smth1 $smth2"
    println(msg)
}
```

## Collections

- Array
```
val langs = arrayOf("kotlin", "java", "go")
```

- List
```
val langs = listOf("kotlin", "java", "go")
```

- Map
```
val langs = mapOf(1 to "kotlin", 2 to "java", 3 to "go")
```

{% hint style=info %}
By default collection type is immutable. Use `mutable...Of()` to make it mutable
{% endhint %}


## vararg
