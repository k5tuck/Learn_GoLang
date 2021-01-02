# Slices

## Topics

- [Creation](#creation)
- [Built-in Functions](#built-in-functions)

Slices are backed by arrays  
Slices are naturally **reference** types (ie. "Copies" will refer to the underlying array)

### [Creation](#topics)

Declaration Styles:

- Literal Syntax to create a slice
- Slice existing array or slice
- `make` function

Literal Syntax

```Go
func main (){
    a := []int{1, 2, 3}
    // b := a
    // b[1] = 5
    fmt.Println(a)
    // fmt.Println(b)
    fmt.Printf("Length: %v\n", len(a))
    fmt.Printf("Capacity: %v\n", cap(a))
}

Output:
[1 2 3]
Length: 3
```

Slicing

```Go
func main (){
    a := []int{1, 2, 3, 4, 5, 6, 7, 8, 9, 10}
    b := a[:] //slice of all elements
    c := a[3:] //slice from 4th element to end
    d := a[:6] // slice first 6 elements
    e := a[3:6] // slice the 4th, 5th, and 6th elements

    // ---- Modified ----
    // Slicing will work with Slices and Arrays
    // a := [...]int{1, 2, 3, 4, 5, 6, 7, 8, 9, 10}
    // a[5] = 42

    fmt.Println(a)
    fmt.Println(b)
    fmt.Println(c)
    fmt.Println(d)
    fmt.Println(e)
}

Output:
[1 2 3 4 5 6 7 8 9 10]
[1 2 3 4 5 6 7 8 9 10]
[4 5 6 7 8 9 10]
[1 2 3 4 5 6]
[4 5 6]
// ---- Modified ----
// [1 2 3 4 5 42 7 8 9 10]
// [1 2 3 4 5 42 7 8 9 10]
// [4 5 42 7 8 9 10]
// [1 2 3 4 5 42]
// [4 5 42]
```

Make Function

```Go
func main (){
    a :=  make([]int, 3, 100) // type, length of slice, capacity
    fmt.Println(a)
    fmt.Printf("Length: %v\n", len(a))
    fmt.Printf("Capacity: %v\n", cap(a))
}

Output:
[0 0 0]
Length: 3
Capacity: 100
```

### [Built-In Functions](#topics)

`len` - returns length of slice  
`cap` - returns length of underlying array  
`append` - add elements to slice

```Go
func main (){
    a := []int{}
    fmt.Println(a)
    fmt.Printf("Length: %v\n", len(a))
    fmt.Printf("Capacity: %v\n", cap(a))
    a = append(a, 1)
    fmt.Println(a)
    fmt.Printf("Length: %v\n", len(a))
    fmt.Printf("Capacity: %v\n", cap(a))
    a = append(a, 2, 3, 4, 5)
    fmt.Println(a)
    fmt.Printf("Length: %v\n", len(a))
    fmt.Printf("Capacity: %v\n", cap(a))
}

Output:
[]
Length: 0
Capacity: 0
[1]
Length: 1
Capacity: 2
[1 2 3 4 5]
Length: 5
Capacity: 8
```

If additional elements exceeds the capacity of the underlying array, this will trigger Go to copy and make a whole new array in a new memory location. After awhile this can become memory expensive.

This is why we use the `make` function, since it addresses the specific capacity of the underlying array.

Concatenating Multiple Slices

```Go
func main (){
    a := []int{}
    a = append(a, []int{2, 3, 4, 5}..., []int{6, 7, 8, 9}...)
    fmt.Println(a)
}

Output:
[1 2 3 4 5 6 7 8 9]
```

Stack Operations

Append - Allows us to push elements onto the Stack
Shift - Allows us to pop elements off the Stack

```Go
func main (){
    a := []int{2, 3, 4, 5}
    fmt.Println(a)
    b := a[1:] // remove element from front
    c := a[:len(a)-1] // remove element from back
    d = append(a[:2], a[3:]...) // remove element from middle
    fmt.Println(b)
    fmt.Println(c)
    fmt.Println(d)
    fmt.Println(a)
}

Output:
[1 2 3 4 5]
[2 3 4 5]
[1 2 3 4]
[1 2 4 5]
[1 2 4 5 5] // need loops for desired result
```
