# Regex tutorial: Email search algorithm

This is a regex tutorial describing how an email regex is used to validate a chain of chaaracters that match the format of an email address.

## Summary

A regex or Regular Expression is made up of a chain of characters and symbols that represents the parameters of a search pattern for text. The email regex specifically validates and checks a user's input to ensure that the entered text represents an email address; the search pattern executes by checking for a sequence of characters, numbers or specified allowed symbols before the @ symbol, followed by a sequence of characters before reaching the closing (.com .net .edu) of an email address.

The regular expression for an email is as follows:

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components

The regex will search for a literal string match, that being said, the entire expression must then be wrapped inbetween two (/) characters for the expression to be responsive and functional. In the expression example at the begining of this gist, you will see that the expression begins and ends with the same (/) character.

### Anchors

There are two anchors in a regular expression, one being the ^ anchor and the other being the $ anchor. The ^ anchor initiates the begining of a string; the validity of the characters that follow are enclosed in square brackets []

* For a string literal match, the square brackets are not used and the search algorithm executes a case sensitive search pattern for the desired match. ^Hello will return a string of any instance that matches "Hello" with a capital "H."  If the user wishes to search for "hello" but the regex is programmed to search for ^Hello, the result will return null due to the fact that a regex is case sensitive.
* If the user wishes to search for a string of potential matches, the user may enter an argument such as [ abc ] this will return a result of either the character "a" the character "b" the character "c" or any combination of the three. The square brackets dissects and seperates the parameters to allow multiple truthy values.

Take a look at the begining of the email regex which begins with the ^ symbol: `/^([a-z0-9_\.-]+)` this represents the parameters of allowed characters before the @ symbol. In this case it allows for a single or series of lowercase letters, numbers, underscores, periods or dashes. The + after the ] bracket represents a quantifier, which will be explained later on in this tutorial.

The closing $ symbol, which ends the search algorithm, only allows characters validated within the opening and closing square brakets: `([a-z\.]{2,6})$/` this argument allows the input of a valid email address closer between the length of two to six characters long with the allowance of lowercase letters and a period.

For example, this search patter will allow email addresses such as:

myemailname42@email.com \
my.email.name42@email.net \
my.emailname42@email.edu

The regex however will not allow characters outside of the search parameter such as:

myemail!#@email.com isn't allowed because the regex does not allow a ! and # symbol \
MyEmail@email.com isn't allowed because the address has a capital M as well as a capital E \
myemail@email.88 isn't allowed because the address ends with the numeric values of 88 \
myemail@email.com! isn't allowed becuase the address has an ! symbol at the end

### Quantifiers

A quantifier sets the limit of characters that your regular expression will match, or will set a limit to an individual section of the string. They are implemented with a minimum and maximum number value into the regex search algorithm; and will match as many occurences of the pattern as possible.

This can be implemented into the regex by using one or more of the following:

* * Will match the pattern zero or more times

* + Will Match the pattern one or more times

* ? Will match the pattern zero or one time

* Curly braces { } will provide three different alternatives to set limits on matches:

    * { 1 } Matches the pattern ONLY 1 time

    * { 1, } Matches the pattern AT LEAST 1 number of times

    * { 1, 5 } Matches the pattern AT LEAST 1 time and A MAXIMUM of 5 times

### Grouping Constructs

### Bracket Expressions

### Character Classes

### The OR Operator

### Flags

### Character Escapes

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
