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

Square brackets match any one of the enclosed characters. You can specify a range of characters by using a hyphen, but if the hyphen appears as the first or last character enclosed in the square brackets it is taken as a literal hyphen to be included in the character class as a normal character.

For example, `[abcd]` is the same as `[a-d]`. They match the "b" in "brisket", and the "a" or the "c" in "arch", but not the "-" (hyphen) in "non-profit".

`^` inside square brackets is a negated or complemented character.That is, it matches anything that is not enclosed in the brackets.

For example, `[^abc]` is the same as `[^a-c]`. They initially match "o" in "bacon" and "h" in "chop".

Contininuing with the code for matching an email:

`[a-z0-9_\.-]`

The guidelines for matching the group. For this code snippet, it can contain letters a-z, numbers 0-9, an underscore, hyphen, or period.The period is an escaped character, so it required the backslash in order to be able to be matched.

### Character Classes

Character classes distinguish kinds of characters such as, for example, distinguishing between letters and digits.Here are some of common character classes:

* `.`  Matches any single character except line terminators.

* `\d` Matches any digit. Equivalent to `[0-9]`.

* `\D` Matches any character that is not a digit. Equivalent to `[^0-9]`.

* `\w` Matches any alphanumeric character, including the underscore. Equivalent to `[A-Za-z0-9_]`.

* `\W` Matches any character that is not a word character. Equivalent to `[^A-Za-z0-9_]`.




### The OR Operator

It is not present in the code for the given matching email code, but in order to talk about the OR Operator, we will look at the following code for matching a hex code.

`/^#?([a-f0-9]{6}|[a-f0-9]{3})$/`

This is a regex for matching a hex code that uses the OR Operator. What this will do is it will match where it starts with the # and that has to come first followed by one of the following:

`[a-f0-9]{6}` which will match a 6 character long string that contains a combination of a-f letters and 0-9 numbers.

`|` OR Operator

`[a-f0-9]{3}` it will match a 3 character long string that contains a combination of a-f letters and 0-9 numbers.

### Flags

A regex flag is not used in the matching email code that is being used for this tutorial.A regular expression typically comes in the form:

`/regex/`

Where the slashes denote where the regular expresssion starts and ends. A flag can be used after the slash to give more guidelines for our matching. The flags are:

* `g`  which stands for "global" which will allow for matching all the instances within a string that follow the matching guidelines set in the regular expression.

* `m` which stands for "multiline" which will search line by line rather than searching through a string as a whole.

* `i` which stands for "insensitive" will make the regular expression case-insensitive, so capitals and lower-case letters will not deture the matching.

### Character Escapes

The backslash `\` in a regex escapes a character that otherwise would be interpreted literally. For example, the open curly brace `{` is used to begin a quantifier, but adding a backslash before the open curly brace `\{` means that the regex should look for the open curly brace character instead of beginning to define a quantifier.

## Author

This tutorial was created by sasan Sahami.

Github: [Github](https://github.com/sasansinson)


