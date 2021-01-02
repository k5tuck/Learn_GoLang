# Constants

## Topics

- [Naming Conventions](#naming-conventions)
- [Typed Constants](#typed-constants)
- [Untyped Constants](#untyped-constants)
- [Enumerated Constants](#enumerated-constants)
- [Enumerated Expressions](#enumerated-expressions)

1. Constants are Immutable, but can also be shadowed
2. They are replaced by the compiler at compile time
   - Value must be able to be calculated at compile time
3. Named like variables - Pascal case for exported constants
   - camelCase for internal constants
4. Typed constants work like immutable variables
   - Can interoperate only w/ same type
5. Untyped constants work like literals
   - Can interoperate with similar types

### [Naming Conventions](#topics)

**Note:** Arrays are inherently going to be mutable (or `var`), so they can't be `const`

```Go
func main(){
    const a int = 88
    fmt.Printf("%v, %T\n", a, a)
}

Output:
88, int
```

### [Typed Constants](#topics)

```Go
func main(){
    const n int = 23
    const o float32 = 3.14
    const p bool = false
    const q string = "bar"
    fmt.Printf("%v, %T\n", n, n)
    fmt.Printf("%v, %T\n", o, o)
    fmt.Printf("%v, %T\n", p, p)
    fmt.Printf("%v, %T\n", q, q)
}

Output:
23, int
3.14, float32
false, bool
bar, string
```

```Go
const n int16 = 19

func main(){
    const n int = 23
    fmt.Printf("%v, %T\n", n, n)
}

Output:
23, int
```

Output:

````

### [Untyped Constants](#topics)

```Go
func main(){
    const a = 62
    var b int16 = 9
    fmt.Printf("%v, %T\n", a+b, a+b) // Compiler sees 62+b
}

Output:
71, int16
````

### [Enumerated Constants](#topics)

`iota` starts at 0 in each `const` block and incements by one  
**Watch out for**: zero const values that are matching zero variable values

```Go
const a = iota // Counter used when creating enumerted constants

func main(){
    fmt.Printf("%v, %T\n", a, a)
}

Output:
0, int
```

```Go
const (
    a = iota  // OR a = iota
    b = iota  // b
    c = iota // c
    // Result will be the same
)

const (
    const a2 = iota
)

func main(){
    fmt.Printf("%v\n", a)
    fmt.Printf("%v\n", b)
    fmt.Printf("%v\n", c)
    fmt.Printf("%v\n", a2)
}

Output:
0
1
2
0
```

### [Enumerated Expressions](#topics)

Bit-Shifting Examples:

Bit-Shifting to translate the size of a file from one format to another

```Go
const (
    _ = iota // ignore first value by assigning to blank identifier
    KB = 1 << (10 * iota)
    MB
    GB
    TB
    PB
    EB
    ZB
    YB
)

func main(){
    filesize := 4000000000.
    fmt.Printf("%.2f GB", filesize/GB)
}

Output:
3.73 GB
```

Bit-Shifting to set Boolean Flags inside a Single byte

```Go
const (
    isAdmin = 1 << iota // 00000001
    isHeadquarters // 00000010
    canSeeFinancials // 00000100

    canSeeAfrica // 00001000
    canSeeAsia // 00010000
    canSeeEurope // 00100000
    canSeeNorthAmerica // 01000000
    canSeeSouthAmerica // 10000000
)

func main(){
    var roles byte = isAdmin | canSeeFinancials | canSeeEurope
    fmt.Printf("%b\n", roles)
    fmt.Printf("Is Admin? %v\n", isAdmin & roles == isAdmin)
    fmt.Printf("Is HQ? %v", isHeadquarters & roles == isHeadquarters)
}

Output:
100101
```
