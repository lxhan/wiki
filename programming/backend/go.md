# Go


### Project structure

```
workspace
+---bin
+---src
    +---github.com
        +---lxhan
            +---go project 1
            +---go project 2
+---pkg
```

## Variables

1. String

```go
var name string = "Alex"
var name = "Alex"
name := "Alex"
```

2. Integer

```go
var age int = 32
var age = 32
age := 32
```

3. Boolean

```go
var isMarried bool = true
var isMarried = true
const isMarried = true
isMarried := true
```

4. Float

```go
var size float32 = 1.3
var size = 1.3
size := 1.3
```

5. Shorthand for multiple vars assignment

```go
name, age := "Alex", 32
```

6. Shorthand for var

```go
name := "Alex"
// Must be inside body
```

7. Get type of variable

```go
fmt.Println("%T\n", name)
// ouputs "string"
```

## Functions

```go
func greet(name string) string {
  return "Hello, " + name
}
```

## Arrays & Slices

1. Arrays

```go
var nameArr \[2\]string

// Declare and assign nameArr := \[2\]string{"Alex", "Lena"}
```

2. Slices
```go
nameSlice := []string{"Alex", "Lena", "etc"}
```

1. Get array/slice length

```go
len(arr)
```

2. Range

```go
arr[1:3]
```

## Conditionals

1. if/else

```go
if x < y {
    fmt.Println("x is less than y")
} else if x > y {
    fmt.Println("x is greater than y")
} else {
  //    
}
```

1. switch

```go
switch color {
    case "blue":
    //
    case "red":
    //
    default:
    //
}
```

## Loops

1. Long method

```go
i := 1
for i <= 10 {
// do smth
}
```

2. Short method

```go
for i := 1; i <= 10; i++ {
// do smth
}
```

3. FizzBuzz

```go
for i := 1; i <= 100; i++ {
    if i % 15 == 0 {
        fmt.Println("FizzBuzz")
    } else if i % 3 == 0 {
        fmt.Println("Fizz")
    } else if i % 5 == 0 {
        fmt.Println("Buzz")
    } else {
        fmt.Println(i)
    }
}
```

## Maps

1. Define map

```go
emails := make(map[string]string)
```

2. Assign key values

```go
emails["alex"] = "alex@gmail.com"
emails["lena"] = "lena@gmail.com"
```

3. Get length

```go
len(emails)
```

4. Delete from map

```go
delete(emails, "alex")
```

5. Shorthand for defining and declaring

```go
emails := map[string]string{"alex":"alex@gmail.com"}
```

## Range

1. Loop through ids

```go
ids := \[\]int{3, 44, 6, 23, 1, 283}

for i, id := range ids {
    fmt.Printf\("%d - id: %d\n", i, id\)
}
```

2. Loop without index
```go
ids := []int{3, 44, 6, 23, 1, 283}

for _, id := range ids {
    fmt.Printf("id: %d\n", id)
}
```

1. Loop through map

```go
emails := map\[string\]string{"alex":"alex@gmail.com", "lena":"lena@gmail.com"}

for k, v := range emails {
    fmt.Printf\("%s: %s\n", k, v\)
}
```
___

## Pointers

1. Declare pointer 
```go
a := 5
b := &a

fmt.Printf("%T\n", b)
fmt.Println(*b)
```

1. Get type of pointer

```go
fmt.Printf("%T\n", b)
```

2. Use \* to read value from address

```go
fmt.Println(*b)
fmt.Println(*&a)
```

3. Change value with pointer

```go
*b = 10
fmt.Println(a)
```

## Closure

```go
func adder() func(int) int {
    sum := 0
    return func(x int) int {
        sum += x
        return sum
    }
}

func main() {
    sum := adder()
    for i := 0; i <= 10; i++ {
        fmt.Println(sum(i))
    }
}
```

## Structs

1. Basic struct

```go
type Person struct {
    firstName string
    lastName string
    age int
}
```

2. Create new struct

```go
person := Person{firstName: "Alex", lastName: "Han", age: 32}
```

3. Shorthand for new struct

```go
person := Person{"Alex", "Han", 32}
```

4. Get property

```go
person.lastName
person.lastName = "Smith"
```

5. Value reciever

```go
func (p Person) greet() string {
    return "Hello, my name is " + p.firstName + "my age is " + strconv.Itoa(p.age)
}
```

6. Pointer reciever

```go 
func (p *Person) getOld() {
    p.age++
}

func (p *Person) changeName(newName string) {
    p.firstName = newName
}
```
___

## Interfaces

```go
type Shape interface {
    area() float64
}

type Circle struct {
    x, y, radius float64
}

func (c Circle) area() float64 {
    return math.Pi * c.radius * c.radius
}

func getArea(s Shape) float64 {
    return s.area
}
```

## Web

```go
import (
    "fmt"
    "net/http"
)

func index(w http.ResponseWriter, r *http.Request) {
    fmt.Fprint(w, "Hello")
}

func main() {
    http.HandleFunc("/", index)
    http.ListenAndServe(":3000", nil)
}
```


## Links
- [Go crash course](https://www.youtube.com/watch?v=SqrbIlUwR0U&t=3193s) 
- [Go full course](https://www.youtube.com/watch?v=YS4e4q9oBaU)
- [Data types](https://www.8host.com/blog/osnovnye-tipy-dannyx-v-go/)
- [Data types cheat sheet](https://rtfm.co.ua/books-translations/go-s-nulya/go-chast-3-tipy-dannyx/)
- [Another data type cheat sheet](https://metanit.com/go/tutorial/2.3.php)
  
