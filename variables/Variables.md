# Variables

## Topics

- [Declaration](#decleration)
- [Redeclaration](#redeclaration)
- [Visibility](#visibility)
- [Naming](#naming)
- [Type Conversions](#type-conversions)

### [Declaration](#topics)

There are 3 ways to declare variables in Go. **All declared variables in Go must be used.**

#### Option 1

- var i int
- i = 42
- i = 27 // Variable can be changed

#### Option 2

- var i int = 42  
  OR
- var (  
   movie string = "42"  
  actorName string = "Chadwick Boseman"  
  characterPortrayal string = "Jackie Robinson"  
  releaseDate int = 2012  
  )

#### Option 3

- i := 42  
  Go Compiler can understand the "needed" data type

### When to Use

You will use **Option** 1 when you want to declare the variable but you are not ready to initialize it yet.

You will use **Option 2** when Go doesn't have enough information to assign the actual type that you want. (ie. Using float32 instead of int or float64) or you are declaring a variable **outside** a function (**_package level_**)

- var number float32 = 29

You will use **Option 3** when expecting an explicit type (ie. int, string, float64) or declaring a variable **inside** a function

### [Redeclaration](#topics)

**"Shadowing"** - Variable with the inner most scope takes precedent.  
Package level declaration is still there, just hidden.

```Go
var i int = 45

func main(){
    fmt.Println(i)
    var i int = 23
    fmt.Println(i)
    i = 11
    fmt.Println(i)
}

Output:
45
23
11
```

### [Visibility](#topics)

There is no **private** scope

#### Package Level Variables

- **Lower case** variables are scoped to **_that_** particular package.

```Go
var num int = 201
func main(){
    fmt.Println()
}
```

- **_Upper case_** variables are scoped to "The Outside World", or are available for other packages to use (**Globally Visible**).

```Go
var Num int = 168
func main(){
    fmt.Println()
}
```

#### Block Scope

- Mainly variables declared inside of functions. Never visible outside of that "block".

```Go

func main(){
    var name string = "Kevin"
    fmt.Println(name)
}
```

### [Naming](#topics)

Pascal or camelCase

- var i int
  - **i** is short (temporary), maybe used for something quick, like a **_for loop_**
- var playerName string
  - **playerName** is longer, used most likely throughout entire app

Length of variable name should reflect the "life" of the variable.

Capitalize acronyms (ie. var theHTTP string, var sleekURL string)

### [Type Conversions](#topics)

The below is an example of converting from a float to an integer; however, the same can also be done in reverse.

**Important Note**: When converting from float to int, it has to explicitly be converted (remember you are losing the decimal portion, possibly resulting in loss of data).

```Go
func main(){
    var i float32 = 38.2
    fmt.Printf("%v, %T\n", i, i)

    var j int
    j = int(i)
    fmt.Printf("%v, %T\n", j, j)
}

Output:

38.2, float32
38, int
```

In order to convert an integer into a string, you must use the `strconv` package. The `Itoa()` function will convert an integer into an ASCII string.

```Go
func main(){
    var i int = 38
    fmt.Printf("%v, %T\n", i, i)

    var j string
    j = strconv.Itoa(i)
    fmt.Printf("%v, %T\n", j, j)
}

Output:

38, int
38, string
```
