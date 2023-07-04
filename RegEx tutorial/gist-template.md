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
A regex is easily indentified by is "/" notiation. Unless it is placed inside a set of slashes it will not be read as an expression, but will instead be read as literal characters. In JavaScript you can also use a constructor to create a regular expression. For example...

The following three examples are of matching URL expressions the first one uses the slash notation to identify it as a regular expression, while the second and third use a JavaScript constructor to achieve those same results.

```
/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/
```

```
const re = RegEx("^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$")
```

```
const re = RegEx(/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/)
```

All three of these examples achieve the same results through different syntax.

### Anchors
The `^` and `$` are both knowns as anchors. The `^` indictes the beginning of the expression and the `$` indicates the end of it. In our URL example we can see that inbetween the slash notation we have `^` marking the start of the expression and the `$` indicating the end.

### Grouping and Capturing
The matching URL expression consists of multiple parts. These parts are split up using parentheses `()`. Each of these sections inside the parentheses are known as subexpression. In our URL example we have four subexpressions that make up the complete expression.

```
(https?:\/\/)
```
```
([\da-z\.-]+)
```
```
([a-z\.]{2,6})
```
```
([\/\w \.-]*)
```

### Bracket Expressions
Now that we have broken down our expression into four subexpressions we can begin to look into the specifics of how this expression functions. Brackets `[]` are used to match a range of characters. Bracket expression are also known positive character groups because they signify the characters that we want to include. In our third subexpression we have `[a-z\.]` the `a-z` signifies that for this part of the expression we would like to search and include any characters from a to z. 

The brackets are used two more times in the URL expression. Once in the second subsection and again in the fourth subexpression. We now know that inside these brackets we are setting parameters for characters we would like to include.

### Quantifiers
Now that we know the brackets are used to establish which characters we would like to include, we can begin to look inside these brackets for specifics in our search. There are a few quantifiers that appear in our URL expression, so lets start of by defining them.

`*` - the wildcard symbol is used to match a pattern zero or more times

`?` - the question mark is used to match a pattern zero or one time (essentially a way of making something 'optional')

`{}` - the curly braces are used to set the limit of characters in a search pattern.

`+` - the plus sign is used to match a pattern one or more times.

#### Wildcard
In our example expression there are two wildcards used at the end.
```
([\/\w \.-]*)*\/?$/
```
The first wildcard is used along with the brackets. This means that that this this range that is set can repeat many times or even not at all. Since this portion is used to determine the 'path' in the URL, this expression allows for the range of characters set inside the brackets to be repeated multiple times or not at all. This simply means that the text set within the `/` used to set the path of the URL is indefinite.

Right after our first wildcard we then get another wildcard meaning that the whole subexpression included within the `()` can repeat multiple times or not at all. This allows multiple `/` to be used to the determine the path in the URL.

#### Question Mark

The question mark quantifier only appears once in our URL expression right at the end of the expression. 
```
([\/\w \.-]*)*\/?$/
```

In this particular example is sets the `/` at the end of the URL as optional. Since a URL can sometimes include a URL at the end of the path this `?` considers that it either may or may not be there.

#### Curly Brackets

The curly brackets are used to set limits. It can be used in four different ways.

`{ n }` - pattern matches exactly 'n' times

`{ n, }` - pattern matches at least 'n' times

`{ n, x }` - pattern matches at least 'n' times and at most 'x' times

`{ , x }` - pattern matches at most 'x' times

In our example this only appears once in our third subexpression.
```
([a-z\.]{2,6})
```

This is used to set a minimum of two and maximum of six characters. In the context of the full expression this means that the domain of the URL must be within this range to be considered valid.

#### Plus Sign
 
 In our expression the `+` only appears once in our second subexpression.
```
([\da-z\.-]+)
```

In this example the `+` is used to say that the URL must include at least one character, within the partucarlar range, after the internet protocol and before the domain name.

### Character Classes

Character classes are a quick and efficient way of filtering out which characters are valid in an expression. Before going into how these classes affect our expression, it is best to define them outside the context of our expression. The following are the two classes that are included in our expression.

`\w` - This expression includes any alphanumeric character from the alphabet including the underscore aswell. (This is a shorthand way of writing the following '[A-Za-z0-9_]')

`\d` - This expression is used to match any digit. (This is a shorthand way of writing '[0-9]')

In the context of our URL expression each of these classes that we defined only appear once. The `\d` appears in our second subexpression.
```
([\da-z\.-]+)
```
This means that our URL name can include any digit or lowercase character for this portion of the URL.

### Character Escapes

### Flags

### Greedy and Lazy Match

### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author

Created by: Alexandre Santos
Github : https://github.com/santos-al
