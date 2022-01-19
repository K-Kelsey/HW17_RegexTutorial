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

The quantifier can be made "lazy" by adding a ? symbol at the end of the request, which will result in returning as few occurences as possible.

Reffering back to the Email Regex: `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/` we recognize that quantifiers are being used at the end of the expression: `\.([a-z\.] {2,6} )$/`, this part of the Regex is used for identifying the .com, .net, or .edu part of the email address. It establishes the amount of characters allowed following the (.) of an email address. In the example here, the expression allows 2-6 characters to follow the closing of the email address. In the same expression you will notice a (.) on the 15th and 29th index of the expression which indicates that the search parameters must result in a match of characters at least one or more times.

Here are a few examples of acceptable and inacceptable email address inputs in regards to the email regex search pattern:

Allowed:

myname@email.com \
myname@email.edu \
myname_88@email-88.net

Not Allowed:

myname@email.emailaddress isn't allowed because it has too many characters after the . closing of the email address \
myname@email.c isn't allowed because it doesn't have enough characters after the . clsoing of the email address \
@email.com is not accepted because there are no characters before the @ symbol and the search requirement that includes the + symbol signifies that the pattern must match at least 1 or more times for the argument to be accepted.

### Grouping Constructs

Grouping constructs are used to compartmentailze different search parameters in a regular expressions, and where those results are placed in the end product of the regex. That being said, the example: myname@email.com will be broken apart into 3 different components of the regex ( myname, email, .com) that satisfy the regex search requiremnets.
Here are the corresponding sections of the email regex:

1. `([a-z0-9_\.-]+)`
2. `([\da-z\.-]+)`
3. `([a-z\.]{2,6})`

If we are refer to the regex as a whole, it will then be considered group 0.

### Bracket Expressions

To target which characters are acceptable in the regex search algorithm, we look for the square bracket [] indicators that represent the acceptable values of the search parameter. These are known as bracket expressions; we create these expressions to identify all acceptable values that we want the expression to match.

The bracket expression: [a-z] will accept the values of "a" the value of "z" and all of the letters that fall inbetween the two values. As a result for this example, the entire alphabet is returned.

Take a look at some of these examples of bracket expressions cans and cannots:
* [a-z] as mentioned, will return us the entire alphabet. However, this will only return us the lowercase values of the alphabet. To include the uppercase values we would add the argument [a-z A-Z] to the expression
* [0-9] will return any variation of the string number values 0-9. This includes 32, 5372, 102 because the expression identifies these numbers by individual value.

In our example of the email regex: `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/` we can see the bracket notations being used in each expression "group".

`/^( [a-z0-9_\.-] +)` accepts the values of any letter between "a" and "z", 1-9, an underscore, period or hyphen.

`( [\da-z\.-] +)` accepts the values of any number, lower case value, period or hyphen. \d represents the numeric string values of [ 0-9 ]

`( [a-z\.] {2,6})$/` uses bracket notation to allow for a lowercase letter or period

Allowed use of bracket expressions:

myname@email.com \
myname8032@email.com \
myname-_.@email.com

Not Allowed based off of the parameters set in the breacket expressions:

myname!@email.com is not accepted becuase the exclamation ! point was not included in the bracket expression. \
myname##@e_mail.com is not accepted because the pound # sign and the underscore _ symbol is not included in the bracket expression. \
myname@.com is not accepted because there are no character values following the @ symbol. \
myname@email.ccccccccccccoooooooooooommmmmmmm is not accepted because there are more than 6 characters after the last period. \

### Character Classes

A character class in regards to a regex identifies an assortment of characters, any of which can occur in an input string to satisfy a match. Although not always, characters classes are more often than not found inbetween the square [] brackets.

Some examples of utilizing character classes are as follows:

* \d identifies the string value of any digit. This class is equivalent to the bracket expression [0-9].

* \D operates in an opposite nature to the \d character class. \D matches all values but excludes the values of 0-9.

* \w identifies any alphanumeric characte, with which includes the underscore _ symbol. This character class example is the same as writing [A-Za-z0-9_].

* \W oporates opposite to the \w character class. This character class matches everything that is not [A-Za-z0-9_].

* \s will match any whitespace, tabs and/or spaces

* \S opposite of the \s character class, will match everything that is not whitespace, tabs, and/or spaces

In the email regex example, we see the inclusion of the character class \d: `([ \d a-z\.-]+)` This example allows the numeric string value of any variation of 0-9.

### The OR Operator

### Flags

### Character Escapes

The forward \ slash indentifies that the character that falls in succession to the \ symbol is a literal interpretation identifier. This allows special characters that are pre-designated with a specific command in a regex, to be used as a character value in the search algorithm.

In the Email Regex example: `/^([a-z0-9_ \. -]+)@([\da-z \. -]+) \. ([a-z \. ]{2,6})$/` the expression uses character escapes in four seperate locations. This parameter will accept a literal period in the string that is returned.

Keep in mind that although the character escapes are used to identify a literal match, character escapes lose their super powers inside bracket expressions. For example, in the subexpression ([\da-z\.-]+), the \d does not represent a literal d match, instead, the forward \ slash represents a numeric string value.

## Author

Thank you for visiting my tutorial, I hope with this walkthrough, you have a better understanding of how an email regex oporates, as well as, how regex works in general! You can find me on github via https://github.com/K-Kelsey or search me by username: K-Kelsey
