# Email Regex Explanation 

Hello my name is Maria Adame and I'm here to explain an email regular expression.

## Summary

I'll be explaining the regular expression for matching a string for an email.  The regular expression will consist of three parts: one for the local part, another for the domain name. We'll be brakigng down the email regex '/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/'. Briefly describe the main points of your contribution. 

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
**Start of string (^)**
'^':Anchors the regex to the start of the string, making sure the email address must start from the beginning of the input.

**Local Part**
'([a-z0-9_\.-]+)': Matches the local part of the email address before the "@" symbol.
'[a-z0-9_\.-]+': Character class matching one or more occurrences of lowercase letters (a-z), digits (0-9), underscores (_), dots (.), or hyphens (-).

**Domain Part**
'([\da-z\.-]+)': Matches the domain part of the email address after the "@" symbol.
'[\da-z\.-]+': Character class matching one or more occurrences of digits (\d), lowercase letters (a-z), dots (.), or hyphens (-).

**Top-Level Domain (TLD)**
'([a-z\.]{2,6})': Matches the top-level domain (TLD) of the email address.
'[a-z\.]{2,6}': Character class matching between 2 and 6 occurrences of lowercase letters (a-z) or dots (.).

These components define the structure of a valid email address and makes sure the regex matches all possible email address variations with the specified format. 

### Anchors

There's going to be two major  anchors in our regex: `^` and `$`. The caret symbol (`^`) asserts position at the start of the string, while the dollar sign (`$`) asserts the end of the string.

`^` Matches the start of the string making sure the regex pattern matches only at the beginning of the input string. What this anchor does in the componte of emails, the caret symbol prevents partial matches where a email address might be found within a longer string

`$` Matches the end of the string making sure the regex pattern matches only at the end of the inout string. What the dollar sign anchor does in terms of email regex, it prevents partial matched where a email adress might be followed by other characters. It also ensures the email adress ends at the end of the string. 

Together these anchors make sure the input string is matched against the email regex pattern and ensuring the email adress is validated from start to finish.

### Quantifiers
`+`: Match one or more occurrences of the preceding element. 
For example:
([a-z0-9_\.-]+): This part matches one or more occurrences of lowercase letters (a-z), digits (0-9), underscores (_), dots (.), or hyphens (-) in the local part of the email address. The + quantifier ensures that there must be at least one character in the local part.
([\da-z\.-]+): This part matches one or more occurrences of digits (\d), lowercase letters (a-z), dots (.), or hyphens (-) in the domain part of the email address. The + quantifier ensures that there must be at least one character in the domain part.

'{2,6}' - matches between 2 and 6 repetitions of the previous character class. In the context of the email regex:
([a-z\.]{2,6}): This part matches between 2 and 6 occurrences of lowercase letters (a-z) or dots (.) in the top-level domain (TLD) of the email address. The {2,6} quantifier allows for flexibility in the length of the TLD, typically ranging from 2 to 6 characters (e.g., ".com", ".org", ".net").


### Grouping Constructs
Group 1: '([a-z0-9_\.-]+)'
This group is for the local part of the email adress before the "@" symbol. For example like 'Name_lastname123' everything before the "@" is being taken accounted for in this group. It's taking to account the lowercased letters (a-z), digits (0-9), underscores (_), dots (.), or hyphens (-).

Group 2: '([\da-z\.-]+)'
This group is for the domain part of the email adress after the "@" symbol. It allows alphanumeric characters and also underscores, dots and hyphens.

Group 3: '([a-z\.]{2,6})'
This group  is used to match the top level domain like .com,.net etc. It allows only 2 and 6 occurrences of lowercases letters (a-z) or dots (.).

### Bracket Expressions
There are three sets of  brackets in this regex pattern.

1. [a-z0-9_\.-]  : This is used to match any lowercase letter (a-z), digit (0-9), underscore (_), dot (.), or dash (-). That's used in Group 1.
2. [\da-z\.-] : This is used to match any digit, lowercase letter, uppercase letter, underscore, dot, and hyphen. It basically represents valid characters that can appear before the @ symbol in an email (Group 2).
3. [a-z\.] :  This is a character class that matches any lowercase letter (a-z), and the dot. It's used and defined more in Group 3. 

These bracket expressions define a set of characters that can appear in each part of the email address. The email regex is defining only the email addresses with the specified character sets.
### Character Classes
There's three specific character  classes used within these bracket expressions:
1. '\d': This character class matches any digit from 0-9. It's used in Group 2 '([\da-z\.-]+)' to match a single alphanumeric character followed by one or more alphanumeric characters, dots, and hypens. 
2. 'a-z': This character class matches any lowercase letter (a-z). This character class can be found in all three groups given the purpose to match lowercase letters can be found in each grouping. 
3. '0-9': This one is also stright foward  and matches any digit from 0 to 9. This can be found in Group 1 '([a-z0-9_\.-]+)'. 

### The OR Operator

1. Within the character class [a-z0-9_\.-], the OR operator is implied between each character or character range. For example:
'a-z': This represents the range of lowercase letters from 'a' to 'z'.
'0-9': This represents the range of digits from '0' to '9'.
'_' : This represents the underscore character.
'\.' : This represents the dot character.
'-' : This represents the hyphen character.

2. Similarly, within the character class [\da-z\.-], the OR operator is implied between each character or character range. For example:
'\d' : This represents any digit from '0' to '9'.
'a-z' : This represents the range of lowercase letters from 'a' to 'z'.
'\.' : This represents the dot character.
'-' : This represents the hyphen character.

These character classes effectively act as if there's an OR operator between each character or character range, allowing any character within the specified range or set to match. This allows the regex to match a wide variety of characters while validating email addresses.

### Flags
There are  no flags specified in this email regex expression pattern.

### Character Escapes
There are two  types of character escapes in this email regex expression pattern:
1. '\d': This escape sequence matches any digit (equivalent to '[0-9]').
2. '\.': This escape sequence matched a literal dot chracter.
You can find these two  escape sequences inside the third group of the regex pattern - "([\.\d-]+)".
These character escapes are used to match specific characters in the regex pattern, allowing for greater flexibility and precision in matching email addresses.

## Author
**Author**: Maria Adame

**GitHub Profile**: https://github.com/adamem02/Candel 


