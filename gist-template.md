# Looking at the Regex for Matching URLs

In the world of regular expressions (regex), there is one pattern that stands out for its versatility and practicality: the regex for matching URLs. This regex expression allows us to validate and extract various components of a URL, such as the protocol, domain name, top-level domain, and additional paths or query strings. By understanding the different elements of this regex and their functionalities, we can gain insights into how it effectively handles URL matching. In this article, we will dive into the intricacies of this powerful regex, exploring anchors, quantifiers, grouping constructs, bracket expressions, character classes, the OR operator, flags, and character escapes, which collectively form the URL matching pattern.

## Summary
The regular expression (regex) that I will be describing is the regex of matching a URL. Components of the regex that will be further elaborated on will be the anchors, quantifiers, grouping constructs, bracket expressions, character classes, The OR operator, flags, and character escapes.

The regex is as follows: `/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`. 

* `/` - Indicate the start and end of the regular expression.
* `^` - Matches the start of a line.
* `(https?:\/\/)?` - Matches the protocol part of the URL (http:// or https://). 
    * The s? means the 's' character is optional, and :\/\/ matches the literal '://'.
* `([\da-z\.-]+)` - This group matches the domain name part of the URL. It consists of one or more characters that can be alphanumeric, dots, or hyphens.
* `\.` - Matches the literal dot in the domain name.
* `([a-z\.]{2,6})` - This group matches the top-level domain part of the URL. It consists of two to six lowercase letters or dots. 
    * This range covers most common domains like .com, .org, .net, etc.
* `([\/\w \.-]*)` - Matches any additional path or query string in the URL. It can contain forward slashes, word characters, spaces, dots, or hyphens. The * means zero or more occurrences of these characters.
* `*` - Matches zero or more occurrences of the previous group.
* `\/?` - Optional trailing slash at the end of the URL.
* `$` - Is the end of a line.
* `/` - Indicates the end of the regular expression.

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
In this particular equation, the ^ and the $ characters are used as an anchor. An anchor is something that lets a program know the string will begin with the characters that follow.

The $ anchor represents the end of a string, meaning it indicates that the string ends with the characters before it, it can be preceded by an exact string or a range of possible matches.

So to start the regex equation, a `^` is used as the second character to tell the program to follow the commands/parameters of everything that follows. Then the equation is closed with a `$` to tell the program that it is done listening for parameters.

### Bracket Expressions
Anything inside a set of square brackets [] represents a range of characters that we want to match. They outline the characters we want to include and all the characters we want to match. 

Hyphens are used between numbers and letters to show that we want to search for a range between the number or letters on either side of the hyphen.

[_-]—The string can contain an underscore or hyphen. In bracket expressions, special characters that we want to include follow alphanumeric character ranges within the brackets.

So `([\da-z\.-]+)` lets the search extend to allow for one or more letters or numbers, dots, and hyphens. As well as `([a-z\.]` which searches for the domain name such as a .com or a .org. The last bracket expression is `[\/\w \.-]`which gets any additional path that may follow the domain, it allows for searching of letters/numbers, spaces, dots, and hyphens.

### Quantifiers
Quantifiers set the limits of what you're searching for inside brackets, they also include the minimum and maximum number of characters that a bracket expression searches for.

In our regex example equation, the {2,6} in the snippit of `([a-z\.]{2,6})` is allowing a minimum of 2 lowercase letters or dots, with a maximum of 6.

To set a limit on the quantifiers, there are multiple characters that you can use to refine the search. Such as:
* *- Matches the pattern zero or more times
* +— Matches the pattern one or more times
* ? — Matches the pattern zero or one time
* {} — Curly brackets can provide three different ways to set limits for a match:
* { n } — Matches the pattern exactly n number of times
* { n, } — Matches the pattern at least n number of times
* { n, x } — Matches the pattern from a minimum of n number of times to a maximum of x number of times

### Grouping Constructs
A way to check multiple parts of a string to determine different sections fulfill different requirements, you use grouping constructs.

The most common way you group a section of a regex is by using parentheses (). Each section within parentheses is known as a subexpression which look for an exact match unless they're told to do otherwise.

Looking at the `(https?:\/\/)` part of the equation, the parentheses start the grouping. `?:` Is a non capturing group which means it looks for the character sequence that does not repeat or used again. 

### Character Classes
Character classes define a set of characters that are used to fulfill a match. 

Common character classes are :
* . — Matches any character except the newline character (\n)
* \d — Matches any numeral digit which is the same as typing [0-9].
* \w — Matches any alphanumeric character including the underscore (_). 
    * This class is equivalent to the bracket expression [A-Za-z0-9_].
* \s — Matches a single whitespace character, including tabs and line breaks

### The OR Operator

In a regular expression (regex), the OR operator is represented by the pipe symbol (|). The OR operator allows you to specify multiple alternatives for matching. The OR operator allows you to create more flexible patterns by providing alternatives for matching. It's important that the OR operator has precedence over other regex operators, so you may need to use parentheses to group expressions properly if needed.

Using the OR operator (|), the expression [abc] could be written as (a|b|c).

### Flags
Flags in a regular expression are optional modifiers that can be added to the end of a regex pattern to change its behavior. They modify how the pattern is matched or searched within a given string. Flags are typically represented as single characters, and they are case-insensitive. Flags are placed at the end of a regex, after the second slash and they define additional functionality or limits for the regex. 

The three most common flags are:
* g — Global search: the regex should be tested against all possible matches in a string.
* i — Case-insensitive search: case should be ignored while attempting a match in a string
* m — Multi-line search: a multi-line input string should be treated as multiple lines

### Character Escapes
Character escapes are special sequences that allow you to match specific characters or character classes. They are denoted by a backslash \ followed by a character or sequence. Character escapes provide a way to represent characters that have special meaning in regex or to match characters that are difficult to type directly. By using character escapes, you can match specific characters or define character classes in your regex patterns to achieve more precise matching.

For example, the open curly brace ({) is used to begin a quantifier, but adding a backslash before the open curly brace (\{) means that the regex should look for the open curly brace character instead of beginning to define a quantifier. This is common when looking for strings with special characters that are the same as a particular component of a regex.

## Author
Collin McCarter is a full stack web development student who wrote this article as a part of exploring computer science for JavaScript. 

Github Profile: https://github.com/collin-mccarter
