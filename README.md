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

### 1.1

**"lexer" vs. "tokenizer" vs. "scanner"?**

https://en.wikipedia.org/wiki/Lexical_analysis

"scanning" / "tokenizing" is the first stage of a lexer

"lexing" involves adding contextual information, like the type of the token, its position in the source code, etc.

**What makes an abstract syntax tree "abstract"?**

https://en.wikipedia.org/wiki/Abstract_syntax_tree

not every detail is captured as-is in the tree

e.g. parentheses are implied by the structure of the tree

### 1.2

What token(s) would we need to add if we were writing a lexer for Python (or another whitespace-sensitive language)?

### 1.3

Parsing Unicode could be complex!

What issues might we encounter if we wanted our lexer to support not just ASCII, but the full Unicode range?

Java allows (letters, \$, _) as the first character of an identifier, but (letter, digit, \$, _) for subsequent characters. How would you implement this in a lexer?