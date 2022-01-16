# Regex tutorial: Email search algorithm

This is a regex tutorial describing how an email regex is used to validate a chain of chaaracters that match the format of an email address.

## Summary

A regex or Regular Expression is made up of a chain of characters and symbols that represents the parameters of a search pattern for text. The email regex specifically validates and checks a user's input to ensure that the entered text represents an email address; the search pattern executes by checking for a sequence of characters, numbers or specified allowed symbols before the @ symbol, followed by a sequence of characters before reaching the closing (.com) of an email address.

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

### Anchors

### Quantifiers

### Grouping Constructs

### Bracket Expressions

### Character Classes

### The OR Operator

### Flags

### Character Escapes

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
