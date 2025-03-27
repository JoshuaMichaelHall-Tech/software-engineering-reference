**Overview**

**Installation**

```
$ gem install rubocop
#or
$ gem install rubocop --version 1.51.0
```
#### Usage
```
$ rubocop hello.rb
```
Running `rubocop` with no arguments will check all Ruby source files in the current directory:

$ rubocop

Alternatively you can specify a list of files and directories to check:

$ rubocop app spec lib/something.rb

You can emulate the behavior of `ruby -wc` as well:

$ rubocop -l

You can autocorrect offenses with `rubocop -a`:

$ rubocop -a

You can limit autocorrect to layout/formatting-related offenses with `rubocop -x`:

$ rubocop -x

RuboCop can do way more. Use `-h` to view all available command-line options.

#### Compatibility

RuboCop supports MRI 2.7+ and JRuby 9.4+.