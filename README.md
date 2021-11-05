# Regex Tutorial

This is an extensive tutorial on regex, how it works, and how to use it

## Summary

The regular expression I will be defining is one that verifies whether or not a string is an e-mail:

    /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

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

    ^([a-z0-9_\.-]+)
    In this context, the '^' means the string must begin with a lowercase letter, digit, dash, or a period.

'$' means the string must end with the characters preceding the symbol

    ([a-z\.]{2,6})$
    This means the string may end with any of the preceeding ranges of characters



### Quantifiers

'*' means the string begins with all character preceding the symbol - with the exception of the last character, where the string can be followed by any number of this (including zero)

'+' means the string begins with all characters preceding the symbol, including the last character - but the last character can repeat

'{}' means the string begins with all characters preciding the symbol; within the bracket contains the number of instances of the last character. {x} means it occurs exactly x times, {x,} means it occurs x or more times, and {x,y} meansit occurs between x and y times

    [a-z\.]{2,6}
    The {2,6} means that the characters within the brackets may appear anywhere from 2-6 times.

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

    ^([\da-z\.-]...
    In this context, this part of a string can bein with a digit (remember the '^' symbol)

'\w' refers to a single letter, number, or underscore

    match: '_', '5', 'z'
    no match: '&'

'\s' refers to a single space

    match: ' '

'.' refers to any single character

    ^[a-z0-9_\.-]+
    Referring to this part of the regex again, the '\.' in combination with the preceding '^' symbol means this string may begin with a period. The '\' is an escape symbol, nullifying any other meaning the '.' has.

'\D', '\W', and '\S' refers to the inverse of their lowercase counterparts

### Flags

'g' is a command that says to keep searching, even after finding a match

'm' is a command that tells '^' and '$' to be in reference to the start and end of a line rather than a string

'i' is a command that tells lowercase and uppercase characters to mean the same thing as their counterparts

### Grouping and Capturing

'()' will group the characters inside the parentheses together, allowing for use of multiple characters for a single command

    ^([a-z0-9_\.-]+)
    The parentheses means that the '^' symbol can refer to any of the symbols within the parentheses (aside from the '+', but for a reason to be explained later)

'?:' allows for the entire

    example: o(?:ne)
    'one' would be a complete match

    example: o(ne)
    'one' would place 'ne' inside its own group

`?<someName>` will simply give a name to the group in question

    example: o(ne) places 'ne' in its own group, while o(?<someName>ne) does the same thing, yet defines said group's name

### Bracket Expressions

'[]' acts the same as OR operators, except it won't acknowledge repeats, even if they're the same characters

    ^[a-z0-9_\.-]
    The brackets in this part of the regex means that the preceding character can any one of the parts within them.

'[x-y]' hyphens will separate the lower and upper limit

    a-z0-9
    These two parts of the regex refer to any lowercase letter from a-z, and any digit from 0-9



### Greedy and Lazy Match

'*', '+', and '{}' will make the match as large as possible.

    ([a-z0-9_\.-]+)
    The '+' here means that the string may begin with (due to the synergy with the '^') the characters within the brackets, with no limit to how many.

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

### Conclusion

The regex may begin with any number of characters as long as they range from 'a-z', '0-9', '_' or '.'

It will then be followed by the '@' character, followed by any number of characters as long as they range from 'a-z', or they are a '.', '-' or a digit.

It will then be followed by a dot as well some digits that range from 'a-z' or a '.' - there may be anywhere from 2-6 of these digits. Afterwards, the string must come to an end.

## Author

My name is Peter Christiansen and I am an aspiring full-stack web developer.

If you have any questions, you can email me at peterjinchristiansen@gmail.com. You can access my other projects at https://github.com/peterjinchristiansen.
