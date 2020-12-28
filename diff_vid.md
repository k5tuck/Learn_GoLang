# Golang First Lesson

## Table of Contents

### Necesseties

1. All go "files" must end in `.go`

### Modules

1.  Must create folder in order to declare a new **module** (Go version of packages)
    - Need files to be "self-contained"
    - Name directory [folder] and file same as package name
    ```Shell
        mkdir cloudy && cd cloudy
        touch cloudy.go
    ```
    - In the terminal in the above folder
    ```
    go mod init github.com/username/repo
    ```
    - Creates **_go.mod_** file
      - Go **_makes_** packages by **_pulling_** from Github repos
    - Back **in** original file "cloudy.go", `package repo`
      - For "ordinary" go files, we will `package main` instead of `package repo`
