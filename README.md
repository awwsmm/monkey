# Writing an Interpreter in Go

Before writing any code

- make sure Go is installed (`brew install go` on macOS)
- create a directory for this project and set up version control (`git init .`)
- create a `go.mod` file in the project root directory with `go mod init monkey`
- install VS Code
- install the Go extension for VS Code offered by Google
- (optional) enable "format on save" in VS Code settings and restart VS Code
- (optional) add `gofmt` pre-commit hook at `.git/hooks/pre-commit`
    - copy from https://github.com/golang/go/blob/release-branch.go1.1/misc/git/pre-commit
    - enable with `chmod +x .git/hooks/pre-commit`

This book uses a TDD style. Has anyone used that before?