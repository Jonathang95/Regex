# REGEX TURTORIAL 


## Summary

In this guide, we will be breaking down the regular expression `/^(https?:\/\/)?([\\da-z\\.-]+)\.([a-z\.]{2,6})([\/\\w \\.-]*)*\/?$/` which is used to validate and match URLs. This regex pattern can match URLs with or without the `http://` or `https://` protocol prefix, followed by a domain name consisting of alphanumeric characters, periods, and hyphens, a top-level domain (TLD) of 2 to 6 characters, and an optional path component that can include slashes, alphanumeric characters, spaces, periods, and hyphens.

```
/^(https?:\/\/)?([\\da-z\\.-]+)\.([a-z\.]{2,6})([\/\\w \\.-]*)*\/?$/
```

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

The `^` and `$` symbols are anchors that match the start and end of the string, respectively. In this regex, they ensure that the entire string matches the pattern.

### Quantifiers

- `?`: Matches the preceding pattern zero or one time. It makes the `(https?:\/\/)?` group optional, allowing for URLs with or without the protocol prefix.
- `+`: Matches the preceding pattern one or more times. It is used in `([\\da-z\\.-]+)` to match one or more alphanumeric characters, periods, or hyphens in the domain name.
- `{2,6}`: Matches the preceding pattern from 2 to 6 times. It is used in `([a-z\.]{2,6})` to match the top-level domain (TLD) of 2 to 6 characters.
- `*`: Matches the preceding pattern zero or more times. It is used in `([\/\\w \\.-]*)*` to match zero or more occurrences of the path component, which can include slashes, alphanumeric characters, spaces, periods, and hyphens.

### OR Operator

The `|` symbol allows for matching one pattern or another.

Example: 
http|https 

In the URL regex, the use of ? is equivalent to the "OR" operator

### Character Classes

- `\d`: Matches any digit character. It is used in `([\\da-z\\.-]+)` to match digits in the domain name.
- `\w`: Matches any word character (alphanumeric characters and underscores). It is used in `([\/\\w \\.-]*)` to match alphanumeric characters and underscores in the path component.
- `\.`: Matches a literal period. It is used in `([\\da-z\\.-]+)` and `([a-z\.]{2,6})` to match periods in the domain name and TLD.

### Flags

Flags modify the behavior of the regex engine. They are placed at the end of the regex pattern, after a closing delimiter (usually `/` in many programming languages).

Example (not in the URL regex,):

```regex
/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/i
```

- `i` - Case-insensitive matching.

### Grouping and Capturing

The parentheses `()` are used for grouping and capturing parts of the pattern:

- `(https?:\/\/)?`: Optional group to match the protocol prefix (`http://` or `https://`).
- `([\\da-z\\.-]+)`: Group to match the domain name.
- `([a-z\.]{2,6})`: Group to match the top-level domain (TLD).
- `([\/\\w \\.-]*)*`: Group to match the path component.

### Bracket Expressions

Bracket expressions `[]` are used to define character classes:

- `[\\da-z\\.-]`: Matches any digit, lowercase letter, period, or hyphen in the domain name.
- `[a-z\.]`: Matches any lowercase letter or period in the top-level domain (TLD).
- `[\/\\w \\.-]`: Matches any slash, word character (alphanumeric or underscore), space, period, or hyphen in the path component.

### Greedy and Lazy Match

Quantifiers are greedy by default, meaning they match as much text as possible. Adding a `?` makes them lazy, matching as little text as possible.

Example in URL regex (note: not explicitly shown in the given regex):

```regex
.*?
```

- Greedy: `.*` matches as much text as possible.
- Lazy: `.*?` matches as little text as possible.

### Boundaries

Word boundaries are used to match positions where a word starts or ends.

Example (not in the URL regex):

```regex
\bword\b
```

- Matches "word" surrounded by word boundaries.

### Back-references

Back-references match the same text as previously matched by a capturing group.

Example (not in the URL regex):

```regex
(\d)\1
```

- Matches two consecutive identical digits.

### Look-ahead and Look-behind

Look-ahead and look-behind assertions match a group before or after a specified pattern without including it in the result.

Example (not in the URL regex):

- Positive look-ahead: `(?=pattern)`
- Negative look-ahead: `(?!pattern)`
- Positive look-behind: `(?<=pattern)`
- Negative look-behind: `(?<!pattern)`

```regex
red(?=bull)
```

- Matches "red" only if it is followed by "bull".

```regex
red(?!bull)
```

- Matches "red" only if it is not followed by "bull".

## Author

Jonathang95
