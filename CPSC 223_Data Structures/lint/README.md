# Style Guide Automation
Author: Eric Yoon '27

## What is a linter?
Linters are tools used to enforce code standards. A linter is able to tell you when your code is not up to spec. Some linters can also fix the problems for you and integrate with your IDE.

If you go into professional software development, your company will likely force you to pass a linter check before you can merge any code.

## Installing `clang-format`
Some smart people made a package called `clang-format` which we will be using.

If you're on Mac and have Homebrew, run the command:
```bash
$ brew install clang-format
```

> If you don't have Homebrew, install it [here](https://brew.sh/). (Hint: you'll need it if you're a CS major!)

> If you're on Windows, best of luck ...

## Setting up your linter rules
Linters are able to accept custom rulesets, which may vary from company to company. I have conveniently made a rule file that covers almost everything in the CPSC 223 style guide.

Copypasta the code below into a file called `.clang-format` at the root of your project directory:
```yaml
# Clang format file to conform to CPSC 223 style guide
# Author: Eric Yoon '27
# License: PUBLIC DOMAIN

ColumnLimit: 80                           # Rule 1
IndentWidth: 4                            # Rule 2
MaxEmptyLinesToKeep: 1                    # Rule 3
SpaceBeforeAssignmentOperators: true      # Rule 4

DerivePointerAlignment: true              # Align * to left/right of space based on coder's preference
SpaceBeforeParens: Never                  # Conform to professors' style of not putting spaces before parens
```

### What's not covered
- Explicit parentheses for long expressions
- Vertical alignment of variable declarations
- Prohibit multiple variable declarations in one line
- Camel/snake case variable naming
- Main function length restriction
- Function docstrings

## Running the linter
To make `clang-format` fix your files in-place, run:

```bash
clang-format -i *.c *.h
```

(When we move into C++, change to `*.cpp`)

### VS Code Integration
You can get [this extension for VS Code](https://marketplace.visualstudio.com/items?itemName=xaver.clang-format) optionally. To run the linter in a file, right click, select `Format document with...` and choose `clang-format`.
