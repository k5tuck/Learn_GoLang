# Structs

## Topics

- [What Are Structs?](#what-are-structs?)
- [Creating Structs](#creating-structs)
- [Naming Conventions](#naming-conventions)
- [Embedding](#embedding)
- [Tags](#tags)

Structs are value types (Use pointers to point to structs you wish to manipulate)  
Normally created as types, but [anonymous structs](#anonymous-structs) are allowed  
No inheritance, use composition via embedding  
Tags added to struct fields to describe fields

### [What Are Structs?](#topics)

Structs are data types that let you gather info together related to one concept with no constraints on the types of data that are contained in the struct.

### [Creating Structs](#topics)

```Go
type Doctor struct {
    number int
    actorName string
    companions[]string
}

func main(){
    aDoctor := Doctor{
            number: 3,
            actorName: "Jon Pertwee",
            companions: []string {
                "Liz Shaw",
                "Jo Grant",
                "Sarah Jane Smith",
            },
    }
    fmt.Println(aDoctor)
    fmt.Println(aDoctor.actorName)
    fmt.Println(aDoctor.companions)
    fmt.Println(aDoctor.companions[1])
}

Output:
{3 Jon Pertwee [Liz Shaw Jo Grant Sarah Jane Smith]}
Jon Pertwee
[Liz Shaw Jo Grant Sarah Jane Smith]
Jo Grant
```

Positonal Syntax **(Encouraged NOT to use)**  
**_If another field is added to the struct, or the order of the fields is changed = Code can possibly Break_**

```Go
type Doctor struct {
    number int
    actorName string
    companions[]string
}

func main(){
    aDoctor := Doctor{
            3,
            "Jon Pertwee",
            []string {
                "Liz Shaw",
                "Jo Grant",
                "Sarah Jane Smith",
            },
    }
    fmt.Println(aDoctor)
}

Output:
{3 Jon Pertwee [Liz Shaw Jo Grant Sarah Jane Smith]}
```

### [Naming Conventions](#topics)

Starts with a Capital letter - exported from package  
Starts with a lowercase letter - internal to package  
No underscores in field names or struct names

```Go
type Doctor struct {
    Number int
    ActorName string
    Companions[]string
    Episodes []string
}

func main(){
    aDoctor := Doctor{
            Number: 3,
            ActorName: "Jon Pertwee",
            Companions: []string {
                "Liz Shaw",
                "Jo Grant",
                "Sarah Jane Smith",
            },
    }
    fmt.Println(aDoctor.Companions)
}

Output:
[Liz Shaw Jo Grant Sarah Jane Smith]
```

#### Anonymous Structs

Used when you need to structure some data you don't have in a normal type (short lived/quick)

```Go

func main(){
    aDoctor := struct{name string}{name: "John Pertwee"}
    anotherDoctor := aDoctor
    anotherDoctor.name = "Tom Baker"
    fmt.Println(aDoctor)
    fmt.Println(anotherDoctor)
}

Output:
{John Pertwee}
{Tom Baker}
```

### [Embedding](#topics)

Composition/Embedding - Allows you to "embed" one struct within another

```Go

type Animal struct {
    Name string
    Origin string
}
type Bird struct {
    Animal // Animal Struct
    SpeedKPH    float32
    CanFly      bool
}

func main(){
    b := Bird{}
    b.Name = "Emu"
    b.Origin = "Australia"
    b.SpeedKPH = 48
    b.CanFly = false

    // Alternative Form - Literal Syntax
    b := Bird{
        Animal: Animal{Name: "Emu", Origin: "Australia"},
        SpeedKPH: 48,
        CanFly: false,
    }

    fmt.Println(b)
    fmt.Println(b.Name)
}

Output:
{{Emu Australia} 48 false}
Emu
```

### [Tags](#topics)

Describes specific information about a field  
You have to use the `"reflect"` package

```Go
package main

import (
    "fmt"
    "reflect"
)

type Animal struct {
    Name string `required max:"100"` // key:"value"
    Origin string
}

func main(){
    t := reflect.TypeOf(Animal{})
    field, _ := t.FieldByName("Name")
    fmt.Println(field.Tag)
}

Output:
required max:"100"
```
