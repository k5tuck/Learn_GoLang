# Loops

## Topics

- [Simple Loops](#simple-loops)
- [Exiting Early](#exiting-early)
- [Looping Through Collections](#looping-through-collections)

For Statement is used for all Loops in Go  
Loops Styles:

- for initializer; test; incrementer {}
- for test {} - Assumes test conditions are being managed somewhere else
- for {} - Runs indefinitely until break statement is called

### [Simple Loops](#topics)

```Go
func main() {
    for i := 0; i < 5; i++ {
        fmt.Println(i)
    }

    // alternative "i" becomes scoped to main function
    // i := 0
    // for ; i<5; i++ {
    //     fmt.Println(i)
    // }
    // fmt.Println(i)

}

Output:
0
1
2
3
4
// Alternative "i" main function scope
0
1
2
3
4
5
```

```Go
func main() {
    for i, j := 0, 0; i < 5; i, j = i+1, j+1 {
        fmt.Println(i, j)
    }
    fmt.Println("----")
    for i, j := 0, 0; i < 5; i, j = i+1, j+2 {
        fmt.Println(i, j)
    }
}

Output:
0 0
1 1
2 2
3 3
4 4
----
0 0
1 2
2 4
3 6
4 8
```

Do/While Loop

```Go
func main() {
    // Go Version of "do/while loops"
    i := 0
    for i < 5 {
        fmt.Println(i)
        i++
    }
}

Output:
0
1
2
3
4
```

### [Exiting Early](#topics)

Infinite For Loop - Using Break

```Go
func main() {
    i := 0
    for {
        fmt.Println(i)
        i++
        if i === 5 {
            break // leaves for loop entirely
        }
    }
}

Output:
0
1
2
3
4
```

Using Continue

```Go
func main() {
    i := 0
    for i := 0 ; i < 10; i++{
        if i %2 == 0 { // When number is even continue is executed
            continue
        }
        fmt.Println(i)
    }
}

Output:
1
3
5
7
9
```

Nested For Loops - Label

```Go
func main() {
Loop:
    for i := 0 ; i < 3; i++{
        for j := 0 ; j < 3; j++{
        fmt.Println(i*j)
        if i*j >= 3 {
            break Loop // break from Label
        }
        }
    }
}

Output:
1
2
3
2
4
6
3
6
9

// Breaking from Label
1
2
3
```

### [Looping Through Collections](#topics)

Collections Available to loop over:  
Arrays, Slices, Maps, Strings, Collections  
`for k, v := range collection {}`

For Range

```Go
func main() {
    s := []int{1,2,3}
    for k, v := range s {
        fmt.Println(k,v)
    }
}

Output:
0 1
1 2
2 3
```

```Go
func main() {
    s := "hello Go!"
    for k, v := range s {
        fmt.Println(k,v)
        fmt.Println(k,string(v))
    }
}

Output:
0 104
0 h
1 101
1 e
2 108
2 l
3 108
3 l
4 111
4 o
5 32
5
6 71
6 G
7 111
7 o
8 33
8 !
```

Syntax works for slices and arrays
