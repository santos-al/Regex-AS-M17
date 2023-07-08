# RegEx Tutorial: Matching a URL

Regular expressions, aka regex, are a specific sequence of characters that are used to define search patterns. They are universal and accessible to any programming language such as JavaScript, Python, and C++ just to name a few. Not are they only very useful for finding specific patterns in text, but also in verfiying user input in applications. If you want to create a program that requires a user to input an email, username, and password you can use regular expression to check if the user input meets a specific pattern. For example, if you want to only accept password with a certain character length you can create a regular expression to check if the user input matches that criteria. 


## Summary

In this post I will be breaking down a URL matching regex. The expression below uses a variety of regex commands to identify a URL within a set of characters.

 Matching a URL:
``` 
/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/
```


## Table of Contents

- [Anchors](#anchors) 
- [Quantifiers](#quantifiers) 
- [Grouping and Capturing](#grouping-and-capturing) 
- [Bracket Expressions](#bracket-expressions) 
- [Character Classes](#character-classes) 
- [Character Escapes](#character-escapes) 

## Regex Components
A regex is easily indentified by its "/" notiation. Unless it is placed inside a set of slashes it will not be read as an expression, but will instead be read as literal characters. In JavaScript you can also use a constructor to create a regular expression.

The following three examples are matching URL expressions. The first one uses the slash notation to identify it as a regular expression, while the second and third use JavaScript constructors to achieve those same results.

```
/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/
```

```
const re = RegEx("^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$")
```

```
const re = RegEx(/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/)
```

All three of these examples achieve the same results through the use of different syntax.

### Anchors
The `^` and `$` are both knowns as anchors. The `^` indictes the beginning of the expression and the `$` indicates the end of it. In our URL example we can see that inbetween the slash notation we have `^` marking the start of the expression and the `$` indicating the end.

### Grouping and Capturing
The matching URL expression consists of multiple parts. These parts are split up using parentheses `()`. Each of these sections inside the parentheses are known as subexpressions. In our URL example we have four subexpressions that make up the complete expression.

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
Now that we have broken down our expression into four subexpressions we can begin to look into the specifics of how this expression works. Brackets `[]` are used to match a range of characters. Bracket expressions are also known positive character groups because they signify the characters that we want to include. In our third subexpression we have `[a-z\.]` the `a-z` signifies that, for this part of the expression, we would like to search and include any characters from a to z. 

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
The first wildcard is used along with the brackets. This means that the range set can repeat many times or even not at all. Since this portion is used to determine the 'path' in the URL, this expression allows for the range of characters set inside the brackets to be repeated multiple times or not at all. This simply means that the text set within the `/` used to set the path of the URL is indefinite.

Right after our first wildcard we then get another wildcard meaning that the whole subexpression included within the `()` can repeat multiple times or not at all. This allows multiple `/` to be used to the determine the path in the URL.

#### Question Mark

The question mark quantifier appears a few times in our URL expression. The first example is in our first subexpression.
```
(https?:\/\/)
```
In this case the internet protocol can either be 'http' or 'https'. Our second instance of this quantifier appears in the final portion of the expression.

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
This means that our URL name can include any digit and/or lowercase character for this portion of the URL. The `\w` then appears once in the fourth subexpression. 
```
([\/\w \.-]*)
```
This character class is used for the 'path' portion of the URL. This means that any alphanumeric character, including the underscore, is valid.

### Character Escapes

Character escapes are used when you need to match a specific character in your regular expression. They can be identified by the `\`.
This specific tool is used multiple times in our URL expression. It appears at least once in each of our subexpressions, so lets take a look at a couple examples.

The first example appears in our first subexpression.
```
(https?:\/\/)
```
These backslashes are used to require two slashes right after the colon in our URL. These character escapes show up again in our fourth subexpression.
```
([\/\w \.-]*)
```
The use of these two character escapes create a match for the `/` in the beginning and at the end for both the `.` and `-`.

## Author

Created by: Alexandre Santos
Github : https://github.com/santos-al
