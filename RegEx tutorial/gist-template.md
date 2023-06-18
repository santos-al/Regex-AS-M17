# RegEx Tutorial: Mathcing a URL

Regular expressions, aka regex, are a specific sequence of characters that are used to define search patterns. They are universal and accessible to any programming language such as JavaScript, Python, and C++ just to name a few. Not are they very useful for finding specific patterns in text, but also in verfiying user input in applications. If you want to create a program that requires a user to input an email, username, and password you can use regular expression to check if the user input meets a specific pattern. For example, if you want to only accept password with a certain character length you can create a regular expression to check if the user input matches that criteria. 


## Summary

In this post I will be breaking down a URL matching regex. This expression below uses a variety of regex commands to identify a URL within a set of characters.

 Matching a URL:
``` 
/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/
```


## Table of Contents

- [Anchors](#anchors) YES
- [Quantifiers](#quantifiers) YES
- [OR Operator](#or-operator) NO
- [Character Classes](#character-classes) YES
- [Character Escapes](#character-escapes) YES
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing) YES
- [Bracket Expressions](#bracket-expressions) YES
- [Greedy and Lazy Match](#greedy-and-lazy-match) YES
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

### Anchors

### Quantifiers

### OR Operator

### Character Classes

### Character Escapes

### Flags

### Grouping and Capturing

### Bracket Expressions

### Greedy and Lazy Match

### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
