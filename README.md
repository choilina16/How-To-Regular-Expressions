# How To: Regular Expressions

What are Regular Expressions?

- Regular expressions, also called a REGEX, are patterns used to match character combinations in strings.
- REGEX can be used to find certain patterns of characters within a string, or to find and replace a character or sequence of characters within a string.
- Frequently used to validate input.

In this Gist, to better help our understanding, we'll be going over the different components of a REGEX. Enjoy!

## Summary

Throughout this Gist, we'll be using the REGEX below as an universal example. At the end of this Gist, you should be able to find out how to decipher the REGEX below.

Matching an Email: `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

## Table of Contents

- [Regex Components](#regex-components)
- [Anchors](#anchors)
- [Bracket Expressions](#bracket-expressions)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [The OR Operator](#the-or-operator)
- [Character Escapes](#character-escapes)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Author + References](#author)

## Regex Components

Let's break down the regex together by using the "Matching an Email" regex.

`Matching an Email: /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

Regex must be wrapped in slash characters (/) as you can see from the example above. This is because a regex is consider to be a literal.

### Anchors

`Matching an Email: /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

`^` & `$` => ANCHORS
`^` anchor signifies the START of a string.
`$` anchor signifies the END of a string.

Also, keep in mind that regex is case sensitive. So, "Lina" does not match "lina".

### Bracket Expressions

`Matching an Email: /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

Bracket Expressions (or also referred to as Positive Character Group):
Anything inside a set of (`[]`) represents a range of characters that we want the email example to match.

`[a-z0-9_\.-]`

If we take a look at the first set of brackets, we can see that we want the beginning of the email to include any combination of letters from `a-z` (all lowercase), numbers from `0-9`, `_`, `\`, `.`, and `-`. The string does not need all of the characters, but must have some combination of them.

- `"Linac9!"` would NOT fulfill the requirement of this regex.
- `"linac9-"` would fulfill the requirement of this regex.

### Quantifiers

Quantifiers set the limit of the string. Most likely, it will represent the minimum and maximum number of characters that your regex will look for.

`{2,6}`
This means that the end of the email should have minimum of `2` characters and maximum of `6` characters.

### Grouping Constructs

With more complicated regex, you might come across a time where you need to check multiple parts of a string with different requirements. This is where grouping constructs come into play. The primary way to do this is by using parentheses (`()`). Each different section you make is called a sub-expression.

`Matching an Email: /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

Looking at our example, let's pull out the different sub-expressions that we see.

- `([a-z0-9_\.-]+)`
- `([\da-z\.-]+)`
- `([a-z\.]{2,6})`

In our example, we have see that we have 3 sub-expressions, meaning different parts of our string has different requirements that we need it to fulfill-- which is extremely common.

### The OR Operator

By adding `|` to the grouping constructs, you give it the same logic as bracket expression. For instance, it's telling the grouping constructs that the string does not need to meet all of the requirements in the pattern.

`[abc]` & `(a|b|c)` work the same way here.

example: `(a|b|c):(x|y|z)`
`"abc:xyz"` and `"acb:xyz"` and `a:z` all match, which `"xyz:abc"` does not.

Unfortunately, our Matching an Email regex does not have any character classes to showcase.

### Character Escapes

By using a backslash (`\`), a character that otherwise would be interpreted literally is escaped.

For example, `{` is used to begin a quantifier. `\{` means that the regex should look for the open curly brace character instead of beginning to define a quantifier.

### Character Classes

Character class = a set of characters.
Common character classes that you should know:

- `.` => matches any character except the newline character (`\n`)
- `\d` => equivalent to `[0-9]`
- `\w` => equivalent to `[A-Za-z0-9_]`
- `\s` => matches a single whitespace character (tabs & line breaks)

`Matching an Email: /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`
In our Matching an Email regex example, the `\d` means that any characters from 0-9 is available to use, `[0-9]`.

### Flags

Regex must be wrapped in slash characters as mentioned in `Regex Components`. One exception to this rule is Flags. Flags are placed at the end of a regex, after the slash. It gives the regex additional functionality or limits.

- `g` => global search
- `i` => case-sensitive search
- `m` => multi-line search

## Author

Author: Lina Choi
Github: [Profile](https://github.com/choilina16)

Please see below for a list of references used to create this Gist.

- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions
- https://coding-boot-camp.github.io/full-stack/computer-science/regex-tutorial

Thank you!
