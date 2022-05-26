# Regular expressions

## Basic Regex

| Symbol | Descriptions                                                              |
| ------ | ------------------------------------------------------------------------- |
| .      | any one character except a line break                                     |
| ?      | 0 or one of the previous character “Colou?r” => Color and Colour          |
| +      | at least one of the previous character “go+gle” => gogle, google, gooogle |
| \*     | 0 or more characters                                                      |
| ^      | start of the string                                                       |
| $      | end of the string                                                         |
| ()     | Groups regular expressions                                                |
| \      | escape character, used to pass special characers "as is"                  |
| [ ]    | any single character from the string inside [ ], example [Dd] => D or d   |
| !      | match characters not in the list, example [!a-z]                          |
| \|     | alternating choices among two or more choices “(c\|s)at” => cat and sat   |

## Ranges

| Range      | Matches                                                  |
| ---------- | -------------------------------------------------------- |
| [0-9]      | any digit                                                |
| [a-z]      | lower-case letters                                       |
| [A-Z]      | upper-case letters                                       |
| []0-9]     | any digit or ], note that ] should be in the first place |
| [aeiou^]   | a vowel or ^                                             |
| [-0-9]     | a dash or any digit                                      |
| [--A]      | any character in the range from - to A                   |
| [aeiou-]   | a vowel or -                                             |
| [a-zA-Z]\* | matches any string of alphabetic characters              |

## Quantity

| Pattern | Matches                              |
| ------- | ------------------------------------ |
| {n,}    | match at least n times               |
| {n}     | match exactly n times                |
| {n,m}   | at least n but not more than m times |

Find all lines that has at least one but no more than 5, ‘c’s - "c\{1,5\}"

## Non-Printing Characters

| Character | Matches                                          |
| --------- | ------------------------------------------------ |
| \r        | line break (carriage return)                     |
| \n        | Unix line break (line feed)                      |
| \t        | tab                                              |
| \f        | page break (form feed)                           |
| \xNN      | hexadecimal character code NN (e.g. \x0D for CR) |
| \\        | backslash                                        |

## Special Characters

| Character | Matches                                                                                |
| --------- | -------------------------------------------------------------------------------------- |
| \s        | any whitespace (space, tab, carriage return, line feed, form feed)                     |
| \S        | any non-whitespace (any character not included by \s)                                  |
| \w        | any word character (a-z, A-Z, 0-9, \_, and some 8-bit characters)                      |
| \W        | any non-word character (all characters not included by \w, including carriage returns) |
| \d        | any digit (0-9)                                                                        |
| \D        | any non-digit character (incl. carriage return)                                        |

## Examples

Find phone numbers in phone.txt file

Possible formats:

```
xxxxxxxxxx

(xxx)xxx-xxxx

xxx-xxx-xxxx

xxx xxx xxxx
```

Search string

```
grep '\(([0-9]\{3\})\|[0-9]\{3\}\)[ -]\?[0-9]\{3\}[ -]\?[0-9]\{4\}' phone.txt
```

Explanation
