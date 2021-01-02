# If and Else

## Topics

- [Operators](#operators)
- [Comparisons](#comparisons)
- [Logical Operators](#logical-operators)
- [If-else and If-else if](#if-else-and-if-else-if)
- [Equality and Floats](#equality-and-floats)

### [Operators](#topics)

Literal Syntax

```Go
func main(){
    if true {
        fmt.Println("The test is true")
    }
    if false {
        fmt.Println("The test is true")
    }
}

Output:
The test is true
// Nothing printed since it's false
```

Initializer Syntax

```Go
func main(){
    statePopulations := map[string]int{
        "California":       39250017,
        "Texas":            27862596,
        "Florida":          20614239,
        "New York":         19745289,
        "Pennsylvania":     12802503,
        "Illinois":         12801539,
        "Ohio":             11614373,
    }
    // if initializer; test
    if pop, ok := statePopulations["Florida"]; ok {
        fmt.Println(pop)
    }
}

Output:
20612439
```

### [Comparisons](#topics)

Work with all numeric type  
String and reference types will use `==` and `!=`

```Go
func main(){
    number := 50
    guess := 30
    if guess < number {
        fmt.Println("Too low")
    }
    if guess > number {
        fmt.Println("Too high")
    }
    if guess == number {
        fmt.Println("You got it!")
    }
    fmt.Println(number<=guess, number>=guess, number!=guess)
}

Output:
Too low
false true true
```

### [Logical Operators](#topics)

```Go
func main(){
    number := 50
    guess := 30
    if guess < 1 || guess > 100 { // Or Operator
        fmt.Println("The guess must be between 1 and 100!")
    }
    if guess >= 1 && guess <= 100 { // And Operator
        if guess < number {
            fmt.Println("Too low")
        }
        if guess > number {
            fmt.Println("Too high")
        }
        if guess == number {
            fmt.Println("You got it!")
        }
        fmt.Println(number<=guess, number>=guess, number!=guess)
    }
    fmt.Println(!true) // Not Operator
}

Output:
The guess must be between 1 and 100! // guess := -5
Too low
false true true
false
The guess must be between 1 and 100! // guess := 105
```

Short-Circuting

```Go
func main(){
    number := 50
    guess := -5
    if guess < 1 || returnTrue() || guess > 100 {
        fmt.Println("The guess must be between 1 and 100!")
    }
    if guess >= 1 && guess <= 100 {
        if guess < number {
            fmt.Println("Too low")
        }
        if guess > number {
            fmt.Println("Too high")
        }
        if guess == number {
            fmt.Println("You got it!")
        }
        fmt.Println(number<=guess, number>=guess, number!=guess)
    }
}

func returnTrue() bool {
    fmt.Println("returning true")
    return true
}

Output:
The guess must be between 1 and 100!
// Does not execute function because true was returned before "returnTrue()" was ever checked in || comparison.
```

### [If-else and If-else if](#topics)

```Go
func main(){
    number := 50
    guess := 105

    if guess < 1 {
        fmt.Println("The guess must be greater than 1!")
    } else if guess > 100 {
        fmt.Println("The guess must be less than 100!")
    } else {
        if guess < number {
            fmt.Println("Too low")
        }
        if guess > number {
            fmt.Println("Too high")
        }
        if guess == number {
            fmt.Println("You got it!")
        }
        fmt.Println(number<=guess, number>=guess, number!=guess)
    }
}

Output:
The guess must be greater than 1! // guess := -3
The guess must be less than 100!  // guess := 105
Too low
false true true
```

### [Equality and Floats](#topics)

Do Not test to see if two floating point numbers are equal to each other  
Turn into comparison operation against an error function  
Divide floats and subtract 1 - If the result is within a tenth of a percent, you can consider them the "same"
