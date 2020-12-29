# Packages in Go

## What is a Package?

A package in Go is basically a **directory** of multiple files. It can provide a single entry/exit point for various functions.
If you have done any programming in JavaScript, it is similar to modules when working with Node.js. It provides a way to import various functions, (**_or features_**), from files that another developer has already created into your program.

Every Go program will have a package assigned to it.
For example for the main file in your root directory might look something like this:

```Go
package main

import "fmt"

func main(){
    fmt.Println("Hello Hello World")
}
```

## What is a Module?

A module is a **directory** that contains Go packages.

- It must be a **VCS** (Version Control System) repo and it should contain at least one Go module.

Example:

```sh
go mod init github.com/username/repo_name
```

- The module should have one or more packages
- A package should have one or more `.go` files in a single directory.

```
root-directory
|-- numbers (package)
|   |-- add.go
|   |-- subtract.go
|   |-- multiply.go
|   |__ divide.go
|-- strings (package)
    |-- upper.go
    |-- lower.go
    |__ capitalize.go
```

## Types of Packages

There are different types of packages that you can call in Go, or rather different "ways" to call packages in Go.

When declaring a package in your Go file, it will be the name of your parent folder.

Example: add.go

```Go
package numbers

import "math"

func add(i int, j int) int {
    i + j
}
```
