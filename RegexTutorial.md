# Regular Expressions (Regex) Tutorial

Regular expressions are patterns used to match character combinations in strings. In this tutorial, we want to see what Regex is and how to use it. With this tool we can search through a body of code or characters and find specific patterns in it to be used for validation.

## Summary

The following code will be used throughout the tutorial to give specific examples for how the components of regex can be used. The following code can be used for matching emails. One use for this code can be used to validate to make sure that an email follows the correct format.

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

Because Regex code is a literal,so we should wrap it in slash characters `/` as you can see in example.

There is one more way to create a Regex object and it is to use RegExp. The details about how RegExp works is not part of this tutorial.

The following two expressions create the same pattern:

`/ab+c/` 

`RegExp('ab+c')` 

### Anchors

The anchor is what starts and ends the regular expression.

*  `^` triggers a string that begins with the exact characters after that. Like `^abc` match `abcot`
*  `$` triggers a string that ends with the exact characters before that. Like `ode$` match `code`

These two anchors also can be triggered by range of possible matches. Our matching email code 

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

is saying that we are looking for something that starts with

`([a-z0-9_\.-]+)`

we will define what everything inside the parentheses later in this tutorial, but what the anchor means is that if we are to find a match it has follow those initial guidelines. It also has to end with

`([a-z\.]{2,6})`

So, it must start and end with the given parameters within the code. If it does not, then it is not a match.



### Quantifiers

A quantifier is used to determine how many times a specific character or group of characters needs to be present in order to have a match.They include the following:

*  `*`- Matches the pattern zero or more times

*  `+`- Matches the pattern one or more times

*  `?`- Matches the pattern zero or one time

*  `{}`- Curly brackets can provide three different ways to set limits for a match:

     *  `{ n }`- Matches the pattern exactly n number of times

     *  `{ n, }`- Matches the pattern at least n number of times

     *  `{ n, x }`- Matches the pattern from a minimum of n number of times to a maximum of x number of times

Quantifiers inherently match as many occurrences of particular patterns as possible unless we add `?` after them,so then they will match as few occurrences as possible. 

if we look at our code for matching the email:

`([a-z0-9_\.-]+)`

this will match any string that contains a-z, 0-9, _, ., or -. The quantifier `+` means that it has to contain at least one of this in order to have a match.

Also in `([a-z\.]{2,6})`

this string has to be between 2 and 6 characters.




### Grouping Constructs

As regular expressions grow more complicated, we may check multiple parts of a string to determine that different sections fulfill different requirements. To break these sections up, we'll need to use grouping constructs.The primary way you group a section of a regex is by using parentheses `()`.

For example `(abc)` looks for an exact match and means order is important in Grouping Construct.

In our email matching code, `([a-z0-9_\.-]+)`  is the first group that appears in our regex. This must be true before moving on to match the next part of the code. `([\da-z\.-]+)`  is the second group that appears in our regex. `([a-z\.]{2,6})`  is the third group that appears in our regex.

When matching, we have to make sure we are following the guidelines of the group before moving on to the next group.

### Bracket Expressions

### Character Classes

### The OR Operator

### Flags

### Character Escapes

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
