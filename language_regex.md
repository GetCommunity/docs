# Regular Expressions

A regular expression is a pattern that the regular expression engine attempts to match in input text. A pattern consists of one or more character literals, operators, or constructs. Regular expression syntax and output may vary by programming language and application.

We use regular expressions to search for and match patterns in text, URLs, within applications like Google Looker Studio, and more to extract and manipulate data.

## Table of Contents

- [Regular Expressions](#regular-expressions)
  - [Table of Contents](#table-of-contents)
  - [Useful Regular Expressions](#useful-regular-expressions)
    - [URLs](#urls)
    - [Images](#images)
    - [Links](#links)
    - [Colors](#colors)

---

## Useful Regular Expressions

### URLs

```regex
http(s)?://(www.).*?/
```

```regex
https://www.[a-zA-Z0-9]*.com
```

```regex
http(s)?://(www.).*?\?utm_source=.*&utm_medium=.*&utm_campaign=.*
```

### Images

```regex
src="(?!(http|https|/))([^"]+)"[^>]*
```

### Links

```regex
href="(?!(http|https|/))([^"]+)"[^>]*
```

### Colors

```regex
#[a-fA-F0-9]{3,6}
```

```regex
rgb\((\d{1,3}), (\d{1,3}), (\d{1,3})\)
```
