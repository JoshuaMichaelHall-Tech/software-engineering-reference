Pronounced (Redjex)

Taken from Launch School Book on Regex
# Conclusion

Fundamental concepts:

- **Patterns** are the building blocks of **regex**. You construct regex from patterns using **concatenation** and **alternation**. You then place the resulting pattern between two `/` characters.
- Concatenation and alternation of two patterns create a new pattern.
- The most basic patterns match a single character, a range of characters, or a set of characters.
- We call some special characters **meta-characters**; they have special meaning inside a regex. When you must match one literally, **escape** it with a leading `\` character.
- **Character class** patterns match any character in a set or range of characters or any combination of sets and ranges.
- **Anchors** force a regex to match at a specific location inside a string.
- A **quantifier** matches a pattern multiple times; they always apply to the pattern to the left of the quantifier. Quantifiers are **greedy** by default, but also have **lazy** forms.
- Parentheses let you combine patterns as a series of alternates. They also provide a way to **capture** parts of a match for later reuse; when used this way, we call the groups **capture groups**. We can access captured values with **backreferences**.

## [Cheat Sheet](https://launchschool.com/books/regex/read/conclusion#cheat-sheet)

In the following tables, unescaped `a`, `b`, and `z` characters denote regular characters (letters, digits, punctuation), while unescaped `p` and `q` characters indicate patterns (each pattern may be arbitrarily complex). Other characters are literals.

### Basic Matching

|Pattern|Meaning|
|---|---|
|`/a/`|Match the character `a`|
|`/\?/`, `/\./`|Match a meta-character literally|
|`/\n/`, `/\t/`|Match a control character (newline, tab, etc)|
|`/pq/`|Concatenation (`p` followed by `q`)|
|`/(p)/`|Capture Group|
|`/(p\|q)/`|Alternation (`p` or `q`)|
|`/p/i`|Case insensitive match|

### Character Classes and Shortcuts

| Pattern          | Meaning                                         |
| ---------------- | ----------------------------------------------- |
| `/[ab]/`         | `a` or `b`                                      |
| `/[a-z]/`        | `a` through `z`, inclusive                      |
| `/[^ab]/`        | Not (`a` or `b`)                                |
| `/[^a-z]/`       | Not (`a` through `z`)                           |
| `/./`            | Any character except newline                    |
| `/\s/`, `/[\s]/` | Whitespace character (space, tab, newline, etc) |
| `/\S/`, `/[\S]/` | Not a whitespace character                      |
| `/\d/`, `/[\d]/` | Decimal digit (`0-9`)                           |
| `/\D/`, `/[\D]/` | Not a decimal digit                             |
| `/\w/`, `/[\w]/` | Word character (`0-9`, `a-z`, `A-Z`, `_`)       |
| `/\W/`, `/[\W]/` | Not a word character                            |

### Anchors

|Pattern|Meaning|
|---|---|
|`/^p/`|Pattern at start of line|
|`/p$/`|Pattern at end of line|
|`/\Ap/`|Pattern at start of string|
|`/p\z/`|Pattern at end of string (after newline)|
|`/p\Z/`|Pattern at end of string (before newline)|
|`/\bp/`|Pattern begins at word boundary|
|`/p\b/`|Pattern ends at word boundary|
|`/\Bp/`|Pattern begins at non-word boundary|
|`/p\B/`|Pattern ends at non-word boundary|

### Quantifiers

| Pattern     | Meaning                                |
| ----------- | -------------------------------------- |
| `/p*/`      | 0 or more occurrences of pattern       |
| `/p+/`      | 1 or more occurrences of pattern       |
| `/p?/`      | 0 or 1 occurrence of pattern           |
| `/p{m}/`    | `m` occurrences of pattern             |
| `/p{m,}/`   | `m` or more occurrences of pattern     |
| `/p{m,n}/`  | `m` through `n` occurrences of pattern |
| `/p*?/`     | 0 or more occurrences (lazy)           |
| `/p+?/`     | 1 or more occurrences (lazy)           |
| `/p??/`     | 0 or 1 occurrence (lazy)               |
| `/p{m,}?/`  | `m` or more occurrences (lazy)         |
| `/p{m,n}?/` | `m` through `n` occurrences (lazy)     |
## **Look Ahead & Look Behind**

| **Assertion** | **Description**                                                                                    |
| ------------- | -------------------------------------------------------------------------------------------------- |
| ?=            | Positive look ahead assertion – matches if the pattern is followed by the specified condition      |
| ?!            | Negative look ahead assertion – matches if the pattern is not followed by the specified condition  |
| ?<=           | Positive look behind assertion – matches if the pattern is preceded by the specified condition     |
| ?<!           | Negative look behind assertion – matches if the pattern is not preceded by the specified condition |
### Meta-characters

|Outside Character Classes|Inside Character Classes|
|---|---|
|`$ ^ * + ? .`|`^ \ - [ ]`|
|`( ) [ ] { }`||
|\| `\` `/`||

### Common Ruby Methods for Regex

| Method            | Use                                             |
| ----------------- | ----------------------------------------------- |
| `String#match`    | Return MatchData with match, or nil. Call to_s. |
| `string =~ regex` | Returns index of first match, or nil            |
| `String#scan`     | Find all regex matches in string, returns array |
| `String#split`    | Split string by regex                           |
| `String#sub`      | Replace regex match one time                    |
| `String#gsub`     | Replace regex match globally                    |

### Common JavaScript Functions for Regex

|Method|Use|
|---|---|
|`String.match`|Determine if regex matches a string|
|`String.split`|Split string by regex|
|`String.replace`|Replace regex match|

### Common Python Methods for Regex

|Method|Use|
|---|---|
|`re.search`|Determine if regex matches a string|
|`re.split`|Split string by regex|
|`re.sub`|Replace regex matches|

## [Variants](https://launchschool.com/books/regex/read/conclusion#variants)

Regex have variants; though most have similarities to each other, the different **engines** also have noticeable differences. For instance, Ruby and Python support the `\A` and `\z` anchors, while JavaScript does not.

Other languages besides the Big Three support regex: Perl, PHP, Awk, C/C++, Java, and more all provide varying levels of support for regex. Even editors like vim, emacs, and Visual Studio Code, as well as command line tools like `sed` and `grep` use regex. Nearly every language and program has a slightly different take on regex, though.

Every regex engine should support the following features:

- basic single character matches, e.g., `/a/`.
- concatenation, e.g., `/pq/`.
- meta-characters escapes, e.g., `/\*/`.
- character classes, e.g., `/[abc]/` and `/[a-m]/`.
- `*` quantifiers, e.g., `/a*/`.
- `.` matches any character except a newline.
- `^` and `$` line (or string) anchors

Other regex engines may not support some of the features we discussed. For instance, `\A`, `\z` and `\Z` aren't available with most older engines. Some features may require escapes to designate meta-characters (the convention today is that we use escapes when we want to match literals). In the Big Three, for example, you can use `/(p|q)/` for alternation, but in `vim`'s default mode, you must use `/\(p\|q\)/` instead.

Some programs even let you specify the engine you want to use. Typically, you have a choice between **basic** (the default), **extended**, and **POSIX** engines. You often find this choice with modern versions of ancient programs like `awk`, `sed`, and `grep`.

Most modern programs cover all or most of the features we have discussed, perhaps with slight variations and various levels of custom enhancements.

## [Resources](https://launchschool.com/books/regex/read/conclusion#resources)

- [Essential Guide To Regular Expressions: Tools and Tutorials](https://www.smashingmagazine.com/2009/06/essential-guide-to-regular-expressions-tools-tutorials-and-resources/)
- [Regular-Expressions.info](https://www.regular-expressions.info/)
- [Regex Tutorial—From Regex 101 to Advanced Regex](https://www.rexegg.com/)

 [Rubular](https://rubular.com/) and [Scriptular](https://scriptular.com/) 

Developers frequently recommend two books as good regex resources:

- [Introducing Regular Expressions](https://shop.oreilly.com/product/0636920012337.do)
- [Mastering Regular Expressions](https://shop.oreilly.com/product/9780596528126.do)

# Examples

## Matching Text with Regular Expressions
```ruby
string = "The quick brown fox jumps over the lazy dog"
index = string =~ /brown/
puts index # Output: 10 remember the index also includes spaces in a string and starts at a 0 index
```

```
string = "The quick brown fox jumps over the lazy dog"
match = /brown/.match(string)
puts match # Output: brown
```

## Character Classes
```
string = "The quick brown fox jumps over the lazy dog"
match = /[aeiou]/.match(string)
puts match # Output: e
```

## Quantifiers 

```
string = "The quick brown fox jumps over the lazy dog"
match = /[aeiou]{2}/.match(string)
puts match # Output: ui
```

## Anchors
```
string = "The quick brown fox jumps over the lazy dog" match = /^The/.match(string) puts match # Output: The
```

### Grouping and Capturing
``` ruby  
string = "John Smith (42)" match = /(\w+)\s(\w+)\s\((\d+)\)/.match(string) puts match[1] # Output: John puts match[2] # Output: Smith puts match[3] # Output: 42
```

## Replacing Text with Regular Expressions
```
string = "The quick brown fox jumps over the lazy dog"
new_string = string.gsub(/brown/, "red")
puts new_string # Output: The quick red fox jumps over the lazy dog
```
