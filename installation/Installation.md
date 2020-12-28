# Installation

## Download Go

Follow this link [Golang Website](https://golang.org/dl/)

### Windows

    - Download Windows file:
        - gox.xx.x.windows-amd64.msi
          (ie. go1.15.6.windows-amd64.msi)
    - Follow Installation Steps
    - Go should install in "C:/Go/bin"

### Linux:

    - Download Linux file:
        - gox.xx.x.linux-amd64.tar.gz
          (ie. go1.15.6.linux-amd64.tar.gz)
    - Navigate to the folder that you installed the above file
    - Extracts contents into your "usr/local/" directory
        - "sudo tar -C /usr/local -xzf go1.15.6.linux-amd64.tar.gz"
        - rm go1.15.6.linux-amd64.tar.gz
    - Open ~/.bashrc (if using bash) or ~/.zshrc (if using zsh) in your favorite text editor
        (ie. nano ~/.bashrc)
    - Navigate to the bottom of the file and insert:
        - export PATH=$PATH:/usr/local/go/bin (This will set the path for your Go executable)
        - export GOPATH=/home/USERNAME/golib
        - export PATH=$PATH:$GOPATH/bin
        (This will set the path for all of your Go package executables)
    - Navigate to Home
        - "cd /home/USERNAME"
        - mkdir golib

### Mac

    - Download Mac file:
        - gox.xx.x.darwin-amd64.pkg
          (ie. go1.15.6.darwin-amd64.pkg)
    - Follow prompts to install
    - Go should install to "/usr/local/go"
    - "usr/local/go/bin" should also be added in your PATH environment variable

## Verify Installation

- Open a Terminal window
- Type: `go version` to see your current version of Go
- Type: `which go` to see where your GO executable is located
