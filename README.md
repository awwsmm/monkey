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

## Chapter 1

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

### 1.4

Adding < and > to our tokens reminds me of HTML: https://stackoverflow.com/a/1732454

HTML is too complex to parse with only regular expressions, you need a parser, like the one we're writing: https://stackoverflow.com/a/1758162

## Chapter 2

### 2.2

yacc, bison, and ANTLR are tools that are commonly used in the programming language development community.

EBNF is all that is needed to automatically define a parser using these tools.

### 2.4

As you read this book and write Monkey code, compare it to the Go code we're using to write the interpreter. Go assignments are very different from Monkey ones (= vs. := operators).

Can anyone think of constructs which are expressions vs. statements in various languages?

Recursive descent is just one kind of parser. Did anyone look into other kinds?

Why are some Go function names uppercase? Uppercase functions are exported, lowercase ones are not.

https://go.dev/tour/basics/3

Note that this applies to fields of structs, as well.

### 2.5

What are all these string placeholders about? (`%q`, `%T`, etc.)

https://gobyexample.com/string-formatting

### 2.6

In the 1960s, a programming language called PL/I had become famous for (apparently) violating these precendence rules.

https://en.wikipedia.org/wiki/Principle_of_least_astonishment

Other than prefix, infix, and postfix, does anyone know of any other kinds of operators?

Error vs Fatal in tests? https://stackoverflow.com/a/24593252 (Fatal aborts early, Error does not)

### 2.7

This GitHub repo seems to contain all of the source code

https://github.com/andriisoldatenko/monkey-go

It's where I found `parser/parser_tracing.go`.

A few more visual examples explaining Pratt parsing:

https://martin.janiczek.cz/2023/07/03/demystifying-pratt-parsers.html