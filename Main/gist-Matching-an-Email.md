# Regex Tuttoial: Matching an Email

There are many ways to validate if a string is a valid email address. Regular Expressions, or regex, are one of the most common ways to do this. This tutorial will show you how to use regex via matching an email address.

## Summary

Briefly summarize the regex you will be describing and what you will explain. Include a code snippet of the regex. Replace this text with your summary.

In short, the regex will be used to match an email address is as below:

```regex
/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/
```

This regex looks like a secret code, but it is short and strong. It is used to validate if a string is a valid email address with syntax string1@string2.string3:

- string1 can contain any lowercase letters, numbers, underscores, dots, or hyphens.
- string2 is the domain, which can contain any lowercase letters, dots, or hyphens.
- string3 is the level domain, which can contain any lowercase letters or dots and the length must be between 2 and 6 characters.

This regex can be used within all programming languages. So it should be learned, and we will learn regex by exploring the components of this regex.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

A regex consists of multiple components to describe the patterns and must be wrapped in slash character (/).

```regex
/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/
```

Below are the regex components.

### Anchors

An anchor is a special character (^ or $) that can be used to match the start or end of a string.

- ^ matches the start of a string, for example, ^Hello means the string must start with "Hello".
- $ matches the end of a string, for example, Hello$ means the string must end with "Hello".

In the "Matching an Email" regex, the string must start with string1 (a string that match the pattern `^[a-z0-9_\.-]+`) and end with string3 ( with the pattern `[a-z\.]{2,6}`).

### Quantifiers

Quantifiers are used to specify the number of times a character or group of characters can appear in a string. They are the following:

- ? means the character or group can appear 0 or 1 time.
- - means the character or group can appear 0 or more times.
- - means the character or group can appear 1 or more times.
- {} can be used to set limits in three different ways as below:
  - {n} means the character or group can appear exactly n times.
  - {n,} means the character or group can appear at least n times.
  - {n,m} means the character or group can appear between n and m times.

In the "Matching an Email" regex, there are quantifiers as below:

- {2,6} in the string3 means the pattern `[a-z\.]` can appear between 2 and 6 times. Because the `[a-z\.]` is the pattern for a string which combines lowercase letters, or dots, this quantifier means the string must contain at least 2 to 6 characters which can be any lowercase letters between a and z, or dots.
- (+) in string2 means the pattern `[\da-z\.-]` can appear 1 or more times. This means the string must contain at least 1 or more characters which can be any lowercase letters between a and z, or digits, or dots, or hyphens.
- (+) in string1 means the pattern `[a-z0-9_\.-]` can appear 1 or more times. This means the string must contain at least 1 or more characters which can be any lowercase letters between a and z, or digits, or underscores, or dots, or hyphens.

### OR Operator

OR operator (|) is used to combine multiple patterns with a logical OR.

In the "Matching an Email" regex, there are OR operators as below:

- [a-z\.] could be written as (a|b|c|d|e|f|g|h|i|j|k|l|m|n|o|p|q|r|s|t|u|v|w|x|y|z|\.)
- [a-z0-9_\.-] could be written as (a|b|c|d|e|f|g|h|i|j|k|l|m|n|o|p|q|r|s|t|u|v|w|x|y|z|0|1|2|3|4|5|6|7|8|9|\_|\.|-)
- [\da-z\.-] could be written as (\d|a|b|c|d|e|f|g|h|i|j|k|l|m|n|o|p|q|r|s|t|u|v|w|x|y|z|\.|-)

### Character Classes

Character classes are used to specify a set of characters. Some of them are the following:

- [] specifies a set of characters.
- \d specifies a digit. This is the same as [0-9].
- \w specifies a word character. This is the same as [a-zA-Z0-9_].

In the "Matching an Email" regex, there are character classes as below:

- [] defines a set of characters for string1, string2, and string3.
- \d defines a digit in string2 - ([\da-z\.-]+). This is the same as [0-9a-z\.]+.

### Flags

Flags are used to modify the behavior of a regex. They are at the end of the regex, after the second slash. They are the following:

- i makes the regex case insensitive.
- m makes the regex multiline.
- g makes the regex global.

### Grouping and Capturing

Each regex can be made by some sections which can be grouped by using parentheses (()). The inside of parentheses is known as subexpression.

In the "Matching an Email" regex, there are 3 subexpressions as /^(subexpression for string1)@(subexpression for string2).(subexpression for string3)$/

### Bracket Expressions

Bracket Expressions are anything inside a set of square brackets ([]). These outline the characters that can appear in a string. For example, [a-z] means any lowercase letter between a and z.

It should be noted that by adding the ^ symbol to the start of the bracket expression, it means the string must not match the bracket expression. For example, [^a-z] means any character that is not a lowercase letter between a and z.

In the "Matching an Email" regex, there are bracket expressions as below:

- [a-z\.] means any lowercase letter between a and z, or dots.
- [a-z0-9_\.-] means any lowercase letter between a and z, or digits, or underscores, or dots, or hyphens.
- [\da-z\.-] means any digit between 0 and 9, or lowercase letter between a and z, or dots, or hyphens.

### Greedy and Lazy Match

Greedy and Lazy match are the way the repetition operators match.

- (+, \*, ?, and {}) are greedy as they match as much as possible and backtrack from there.
- (+?, \*?, ??, and {}?) are lazy as they match as little as possible, matching more only when the remaining string does not match the smaller pattern.

In the "Matching an Email" regex, there are greedy and lazy match as below:

- [a-z0-9_\.-]+ is greedy match
- [\da-z\.-]+ is also greedy match

### Boundaries

Boundaries are markers, used to enforce the boundaries of a regex such as ^ and $. They can be used to match the start or end of a string.

In the "Matching an Email" regex, the boundaries and the grouping together define the structure of an email as start with string1 and end with string3 looks like string1@string2.string3.

### Back-references

Back-references are used to refer to a previously matched subexpression. They are written as \n with n=1, 2, 3, and so on.

In the "Matching an Email" regex, there is no back-references. However, if we use ([a-z0-9_\.-]+)\1, it will match something like string1string1

### Look-ahead and Look-behind

Look-ahead and Look-behind are used to match something ahead or behind a regex. They are written as (?=) and (?<=); and negative look-ahead and negative look-behind are written as (?!) and (?<!).

In the "Matching an Email" regex, there is no look-ahead and look-behind, but for example with (?!\d), the updated regex .([a-z\.]{2,6}(?!\d))$/ can exclude the top level domain ending with number which is not a valid domain.

## Author

Dinh Nguyen - [https://github.com/DinhN17](https://github.com/DinhN17)
