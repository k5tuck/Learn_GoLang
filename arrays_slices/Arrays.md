# Arrays

## Topics

- [Creation](#creation)
- [Built-in Functions](#built-in-functions)

Arrays are considered: values  
Arrays must have a **_fixed_** value at compile time  
Most Commonly Used to back **_slices_**

### [Creation](#topics)

Declaration Styles:

- a := [3]int{1, 2, 3}
- a := [...]int{1, 2, 3}
- var a [3]int

```Go
func main (){
    grades := [3]int{100, 63, 82}
    // Alternative Option:
    // grades := [...]int{100, 63, 82}
    fmt.Printf("Grades: %v", grades)
}

Output:
Grades: [100, 63, 82]
```

```Go
func main (){
    var students [3]string
    fmt.Printf("Students: %v\n", students)
    students[0] = "Lisa"
    students[1] = "Sally"
    students[2] = "Trista"
    fmt.Printf("Students: %v", students)
    fmt.Printf("Student #1: %v", students[1])
}

Output:
Students: []
Students: [Lisa Sally Trista]
Student #1: Sally
```

An Array can only hold one data type and will be formatted liek so:
[size of array]data array will store (ie. string, int, float64){values for array}

### [Built-In Functions](#topics)

`len` - Length Built-In Function (returns size of array)

```Go
func main (){
    var students [5]string
    students[0] = "Lisa"
    students[1] = "Sally"
    students[2] = "Trista"
    fmt.Printf("Number of Students: %v", len(students))
}

Output:
Number of Students: 5
```

```Go
func main (){
    var identityMatrix [3][3]int = [3][3]int{[3]int{1,0,0}, [3]int{0,1,0}, [3]int{0,0,1 }}
    // Alternative Option:
    // var identityMatrix [3][3]int
    // identityMatrix[0] = [3]int{1,0,0}
    // identityMatrix[1] = [3]int{0,1,0}
    // identityMatrix[2] = [3]int{0,0,1}
    fmt.Println(identityMatrix)
}

Output:
[[1 0 0] [0 1 0] [0 0 1]]
```

Copies refer to underlying data

```Go
func main (){
    a := [...]int{1, 2, 3}
    b := a // Literal copy of the array
    // ----------------------------
    // Alternative Method - Pointers:
    // b := &a
    // b "points" to the exact data stored at a
    // ----------------------------
    b[1] = 5
    fmt.Println(a)
    fmt.Println(b)
}

Output:
[1 2 3]
[1 5 3]

// Alternative Method:
[1 5 3]
&[1 5 3]
```
