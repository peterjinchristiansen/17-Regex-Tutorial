# Regex Tutorial

This is an extensive tutorial on regex, how it works, and how to use it

## Summary

Briefly summarize the regex you will be describing and what you will explain. Include a code snippet of the regex. Replace this text with your summary.

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

### Anchors

'^' means the string must begin with the characters succeeding the symbol

    example: ^one
    match: 'onetime'
    no match: 'once'

'$' means the string must end with the characters preceding the symbol

    example: one$
    match: 'none'
    no match: 'onee'

### Quantifiers

'*' means the string begins with all character preceding the symbol - with the exception of the last character, where the string can be followed by any number of this (including zero)

    example: one*
    match: 'oneeeeeeee', 'on'

'+' means the string begins with all characters preceding the symbol, including the last character - but the last character can repeat

    example: one+
    match: 'one', 'oneeeeeeeeeeeee'
    no match: 'on'

'{}' means the string begins with all characters preciding the symbol; within the bracket contains the number of instances of the last character. {x} means it occurs exactly x times, {x,} means it occurs x or more times, and {x,y} meansit occurs between x and y times

    example: one{3}
    match: 'oneee'
    no match: 'onee'

    example: one{3,}
    match: 'oneee', 'oneeeeeeeeee'
    no match: 'onee'

    example: one{2,4}
    match: 'onee', 'oneeee', 'oneee'
    no match: 'on', 'oneeeee'

### OR Operator

'|' will take in the character before and after, and either one of those can be the condition

    example: on|e
    match: 'oe', 'onnnnnnnnn'
    partial: 'onnnne' (last characters not included)

### Character Classes

'\d' refers to a single digit

    match: '4'
    partial: '41'
    no match: 'four'

'\w' refers to a single letter, number, or underscore

    match: '_', '5', 'z'
    no match: '&'

'\s' refers to a single space

    match: ' '

'.' refers to any single character

'\D', '\W', and '\S' refers to the inverse of their lowercase counterparts

### Flags

'g' is a command that says to keep searching, even after finding a match

'm' is a command that tells '^' and '$' to be in reference to the start and end of a line rather than a string

'i' is a command that tells lowercase and uppercase characters to mean the same thing as their counterparts

### Grouping and Capturing

'()' will group the characters inside the parentheses together, allowing for use of multiple characters for a single command

    example: ^(on)
    match: 'one'
    no match: 'oen'

'?:' allows for the entire 

    example: o(?:ne)
    'one' would be a complete match

    example: o(ne)
    'one' would place 'ne' inside its own group

`?<someName>` will simply give a name to the group in question

    example: o(ne) places 'ne' in its own group, while o(?<someName>ne) does the same thing, yet defines said group's name

### Bracket Expressions

'[]' acts the same as OR operators, except it won't acknowledge repeats, even if they're the same characters

    example: o[ne]
    match: 'on'
    partial: 'onnnne' (only the first two characters)

'[x-y]' hyphens will separate the lower and upper limit

    example: [1-6] references the numbers 1, 2, 3, 4, 5, or 6

    example: [a-e] references the letters a, b, c, d, e

    example: [a-z] references all lowercase letters


### Greedy and Lazy Match

'*', '+', and '{}' will make the match as large as possible.

    example: x+y
    complete match: 'xy333333333yxy333333333y'

'?' will negate this:

    example: x+?y
    partial match: 'x33y333333333yxy333333333y'
    the match: 'x33y'

### Boundaries

'\b' will only match if the string ([begins or ends], depending on [starting with \b or ending with \b]) with a word character

*remember, a word character is a number, letter, or underscore

    example: \b123\b
    match: '123'
    no matches in here: 'test 123test'

    example: \b123
    match: '123', '123test'
    no matches: 'test123'

    example: 123\b
    match: '123', 'test123'
    no matches: '123test'

\B will only match if it's only surrounded by word characters

    example: \B123\B
    match: test123test
    no match: 123test

### Back-references

'\x' will be set equal to the text in a group called 'x'. For example, if a group is defined as '1', then '/1' refers to the exact string contained within the group

### Look-ahead and Look-behind

'?=' will match something only if it's succeeded by something else

    example: o(?=n)
    match: 'on'
    no match: 'no', 'o'

'?<=' will match something only if it's preceded by something else

    example: o(?<=n)
    match: 'no'
    no match: 'on', 'o'

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
