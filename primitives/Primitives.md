# Primitives

## Topics

- [Booleans](#booleans)
- [Numeric Types](#numeric-types)
- [Text Types](#text-types)

### [Booleans](#topics)

```Go
func main (){
    var b bool = true
    fmt.Printf("%v, %T\n", b, b)
}

Output:

true, bool
```

Not an **alias**  
Zero Value is false  
Normally used as "state" flags  
More Commonly used for **_Logical Tests_**

Logical Test Example

```Go
func main (){
    k := 9 == 9
    t := 31 == 9
    fmt.Printf("%v, %T\n", k, k)
    fmt.Printf("%v, %T\n", t, t)
}

Output:

true, bool
false, bool
```

### [Numeric Types](#topics)

1. [Integers](#integers)
2. [Floating Points](#floating-points)
3. [Complex Numbers](#complex-numbers)

Can't mix types in same family (ie. int8 and int16, float32 and float64)

#### [Integers](#numeric-types)

When initializing `int` if no value is assigned, value = 0

(Signed - has plus and minus) `int` will always at least be 32 bits and the default integer type

- int8 ranges from: -128 to 127
- int16 ranges from: -32,768 to 32,767
- int32 ranges from: -2,147,483,648 to 2,147,483,647
- int64 ranges from: -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807

(Unsigned - can only be positive) `uint` - bytes

- unint8 rangers from: 0 to 255
- unint16 ranges from: 0 to 65,535
- unint32 ranges from: 0 to 4,294,967,295

```Go
func main (){
    var n unint16 = 24
    fmt.Printf("%v, %T\n", n, n)
}

Output:
24, uint16
```

```Go
func main (){
    a := 10
    b := 3
    fmt.Println(a + b) // add
    fmt.Println(a - b) // subtraction
    fmt.Println(a * b) // multiplication
    fmt.Println(a / b) // division
    fmt.Println(a % b) // remainder
}

Output:
13
7
30
3
1
```

```Go
func main (){
    a := 10 // 1010
    b := 3 // 0011
    fmt.Println(a & b) // 0010 - and
    fmt.Println(a | b) // 1011 - or
    fmt.Println(a ^ b) // 1001 - xor
    fmt.Println(a &^ b) // 0100 - not
}

Output:
2
11
9
8
```

Bit-Shifting

```Go
func main (){
    a := 8 // 2^3
    fmt.Println(a << 3) // 2^3 * 2^3 = 2^6 = 64
    fmt.Println(a >> 3) // 2^3 / 2^3 = 2^0 = 1
}

Output:
64
1
```

#### [Floating Points](#numeric-types)

Types: 32bit and 64bit Versions  
Styles:

- Decimal (3.56)
- Exponential (12e20 or 3E10)
- Mixed (16.4e11)

`float64` will be the default float

- float32 ranges from: +-1.18E-38 to +-3.4E38
- float64 ranges from: +-2.23E-308 to +-1.8E308

```Go
func main (){
    i := 3.14
    i = 13.7e72
    i = 2.1E14
    fmt.Printf("%v, %T\n", i, i)
}

Output:

2.1e+14, float64
```

```Go
func main (){
    a := 10.2
    b := 3.7
    fmt.Println(a + b)
    fmt.Println(a - b)
    fmt.Println(a * b)
    fmt.Println(a / b)
}

Output:
13.89999999
6.499999999
37.74
2.756756756
```

#### [Complex Numbers](#numeric-types)

Types: `complex64` and `complex128`  
Zero Value: (0+0i)  
Built-in Functions:

- complex - make a complex number from two floats
- real - get the real number as a flaot
- imag - get the imaginary number as a float

Complex64 will produce float32 (float32 + float32 = complex64)  
Complex128 will produce float64 (float64 + float64 = complex128)

```Go
func main (){
    var k complex64 = 1 + 2i
    fmt.Printf("%v, %T\n", i, i)
    fmt.Printf("%v, %T\n", real(i), real(i))
    fmt.Printf("%v, %T\n", imag(i), imag(i))
}

Output:

(1+2i), complex64
1, float32
2, float32
```

```Go
func main (){
    var k complex128 = complex(9, 11)
    fmt.Printf("%v, %T\n", i, i)
}

Output:

(9+11i), complex128
```

```Go
func main (){
    b = 1 + 2i
    c = 2 + 5.2i
    fmt.Println(b + c)
    fmt.Println(b - c)
    fmt.Println(b * c)
    fmt.Println(b / c)
}

Output:

(3+7.2i)
(-1-3.2i)
(-8.4+9.2i)
(0.39948453360824742-0.038659793814433i)
```

### [Text Types](#topics)

Strings

- Any utf-8 character
- Immutable
- Concatenated with (+) operator
- Can be converted to []byte

```Go
func main(){
    s := "this a string yo"
    fmt.Println("%v, %T\n", s, s)
    fmt.Println("%v, %T\n", s[2], s[2])
    fmt.Println("%v, %T\n", string(s[2]), s[2])
}

Output:

this a string yo, string
105, uint8
i, uint8
```

```Go
func main(){
    s := "this a string yo"
    b := []byte(s)
    fmt.Println("%v, %T\n", b, b)
}

Output:

[116 104 105 115 32 97 32 115 116 114 105 110 103 32 121 111], []uint8
```

Runes

- Any utf32 character
- When declaring must use single `'` quotes `'`
- Alias for int32
- Special methods required to process (ie. strings.Reader#ReadRune)

```Go
func main(){
    r := 'a'
    fmt.Println("%v, %T\n", r, r)
}

Output:

97, int32
```
