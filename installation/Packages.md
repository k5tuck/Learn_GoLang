# Packages in Go

## What is a Package?

A package in Go is basically a **directory** of multiple files, that that provides a single entry/exit point for various functions.
If you have done any programming in JavaScript, it is similar to modules when working with Node.js. It provides a way to import various functions, (**_or features_**), from files that another developer has already created.

Every Go program will have a package assigned to it.

## What is a Module?

A module is a **directory** that contains Go packages.

- It must be a **VCS** (Version Control System) repo or it should contain at least one Go module.
- The module should have one or more packages
- A package should have one or more `.go` files in a single directory.

```
root-directory
|-- numbers
|   |-- add.go
|   |-- subtract.go
|   |-- multiply.go
|   |__ divide.go
|-- strings
    |-- upper.go
    |-- lower.go
    |__ capitalize.go
```

## Types of Packages

There are different types of packages that you can call in Go, or rather different "ways" to call packages in Go.
