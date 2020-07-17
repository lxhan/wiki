# Notes on Kotlin 

## Variables

- Mutable: `var`
- Immutable: `val`

{% hint style=info %}
Visibility of vars, funs etc is public by default
{% endhint %}

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

{% hint style=info %}
By default collection type is immutable. Use `mutable...Of()` to make it mutable
{% endhint %}

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
langs.forEachIndexed {index, lang -> 
    println("$lang is at index $index")
}
```

## vararg

- String

```kt
fun saySmth(smth: String, vararg items) {
    items.forEach { item ->
        println("$smth $item") 
    }
}

fun main() {
    saySmth(smth: "Hey")
    saySmth(smth: "Hey", ...items: "Kotlin", "Java", "Go")
}
```

- Spread operator

```kt
fun main() {
    saySmth(smth: "Hey", *items)
}
```

## Named arguments

```kt
fun saySmth(greet: String, name: String) = println("$greet $name")

fun main() {
    saySmth(greet = "Hi", name = "Alex")
}
```

## Default values for arguments

```kt
fun saySmth(greet: String = "Hi", name: String) = println("$greet $name")

fun main() {
    saySmth(name = "Alex")
}
```

## Classes

- Full syntax

```kt
class Person(_name: String, _age: Int) {
    val name: String
    val age: Int
    
    init {
        name = _name
        age = _age
    }
}
```

- Short syntax

```kt
class Person(val name: String, val age: Int) {

}
```

- Secondary constructor

```kt
class Person(val name: String, val age: Int) {
    constructor(): this("Alex", 33) {
         
    }
}
```

{% hint style=info %}
Init block will always run before secondary constructor
{% endhint %}

- Properties

```kt
class Person(val name: String = "Alex", val age: Int = "33") {
    var job: String? = null
}
```

- Methods

```kt
class Person(val name: String = "Alex", val age: Int = "33") {
    var job: String? = null
    
    fun getFullInfo() {
        val jobCheck = job ?: "no job" 
        println("$name, $age, $job") 
    }
}
```

- Override getter and setter

```kt
class Person(val name: String = "Alex", val age: Int = "33") {
    var job: String? = null
        set(value) {
            field = value
            println("overriding setter")
        }
        
        get() {
            println("overriding getter")
            return field
        }
}
```

- `internal` - means that class is public within the module

- `protected` - means that class will be available with the class or subclasses

- `open` - to make a class inheritable


## Interfaces

- Basic interface

```kt
interface PersonInfoProvider {
    fun printInfo(person: Person)
}

class BasicInfoProvider : PersonInfoProvider {
    override fun printInfo(person: Person) {
        println("info") 
    }
}

fun main() {
    val provider = BasicInfoProvider()
    
    provider.printInfo(Person())
}
```

- Overriding interface

```kt
interface PersonInfoProvider {
    val providerInfo: String
    
    fun printInfo(person: Person) {
        println(providerInfo) 
    }
}

class BasicInfoProvider : PersonInfoProvider {
    override val providerInfo: String
        get() = "BasicInfoProvider"
        
    override fun printInfo(person: Person) {
        super.printInfo(person)
    }
}
```

- Check interface

```kt
if (infoProvider is PersonInfoProvider)
if (infoProvider !is PersonInfoProvider)
```

- Casting

```kt
(infoProvider as PersonInfoProvider).printInfo()
```

## Object expressions

```kt
val provider = object : PersonInfoProvider {
    override val providerInfo: String
        get() = "new info"
}
```

## Companion objects

```kt
class Entity private constructor(val id: Int) {
    companion object {
        const val pId = 23
        fun create() = Entity(id) 
    }
}

fun main() {
    val entity = Entity.create()
    
    println(Entity.pId)
}
```

## Object declarations

```kt
object EntityFactory {
    fun create() = Entity(23)
}
```

## Enum class

```kt
enum class EntityType {
    EASY, MEDIUM, HARD
    
    fun getFormattedName() = name.toLowerCase().capitalize() 
}
```

## Sealed class

```kt
sealed class Entity() {
    data class Easy(val id: String, val name: String): Entity()
    data class Medium(val id: String, val name: String): Entity()
    data class Hard(val id: String, val name: String, val multiplier: Float): Entity()
}

object EntityFactory {
    fun create(type: EntityType) : Entity {
        val id = UUID.randomUUID().toString()
        val name = when(type) {
            EntityType.EASY -> type.name
            EntityType.MEDIUM -> type.getFormattedName()
            EntityType.HARD -> "Hard"
        }
        
        return when (type) {
            EntityType.EASY -> Entity.Easy(id, name) 
            EntityType.MEDIUM -> Entity.Medium(id, name) 
            EntityType.HARD -> Entity.Hard(id, name, multiplier: 2f) 
        }
    }
}
```

## Advanced functions

- Higher order functions

```kt
fun printFilteredStrings(list: List<String>, predicate: (String) -> Boolean) {
    list.forEach {
        if (predicate(it)) {
            println(it) 
        }
    }
}

fun main() {
    val langs = listOf("Kotlin", "Java", "Python")
    printFilteredStrings(langs, {it.startsWith("K")})
    
    printFilteredStrings(langs) {
        it.startsWith("P") 
    }
}
```

- Filter

```kt
langs
    .filterNotNull()
    .filter {
        it.startsWith("P") 
    }
    .forEach {
        println(it) 
    }
```

- Map

```kt
langs
    .map {
        it.length 
    }
```

- Take

```kt
langs.take(3)

langs.takeLast()
```

- Associate

```kt
val map = langs
    .filterNotNull()
    .associate { it to it.length }
    .forEach { // it: Map.Entry<String, Int>
        println("${it.value}, ${it.key}") 
    }
```

- Find

```kt
val lang = langs.filterNotNull().find { it.startsWith("Java") }
```

- Empty

```kt
val lang = langs.filterNotNull().findLast { it.startsWith("Java") }.orEmpty()
```
