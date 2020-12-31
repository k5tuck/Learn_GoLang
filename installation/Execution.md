# Executing Go Files

## Ways to execute your file

To run a `.go` file you have three options:

1. `go run` path-to-file (ie. src/github.com/k5tuck/repo_name)
2. `go build` package location (ie. github.com/k5tuck/repo_name)
3. `go install` package location (ie. github.com/k5tuck/repo_name)

## Go Run

The go run command will run the file locally, and can be executed like so:

- `go run path-to-file`
  - Example:
    - go run src/github.com/k5tuck/repo_name

## Go Build

The go build command will build an executable file and place it in the root directory, and can be executed like so:

- `go build package location`
  - Example:
    - go build github.com/k5tuck/repo_name

## Go Install

The go run command will build an executable and place it in the "bin" directory under your GOPATH, and can be executed like so:

- `go install package location`
  - Example:
    - go install github.com/k5tuck/repo_name
