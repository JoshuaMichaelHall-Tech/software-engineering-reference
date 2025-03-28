QUESTIONS (FROM SPOT WIKI)

# RB109 Written Questions - From Christian Larwood's Blog

Edited by Joshua Hall

Suggested response format (based on feedback from other students & Srdjan’s blog post):

- What does the code output? What are the return values?
- Answer the why behind the output/return:
    - Focus only on the lines of code that deliver the output and return values.
- Summarize what the problem demonstrates and why:
	- This problem demonstrates the concept of local variable scope/etc…
    - This can be at the beginning or end of your answer - personal preference.

Using Markdown: use `backticks` (Markdown formatting) to highlight variable names, methods, and anything in the code to which you refer (but not line numbers). Example: On line 5 variable `fruit` is initialized to the value of `'strawberry'`. For blocks of code, use three `backticks` with the word 'ruby' (\`\`\`ruby) on the line preceding the block of code, and three more `backticks` (\`\`\`) on the line after the block of code. This will create a formatted box for your code which looks like a terminal containing your code. Please enter an additional newline before and after the code box for added readability. Example:

(newline)
\`\`\`ruby
(your code here)
\`\`\`
(newline)

**Always aim to answer: What does the following code output and return? Why? What concept does it demonstrate?**

## Local Variable Scope

### Example 1
What does the following code return? What does it output? Why? What concept does it demonstrate?

```Ruby
a = “Hello”
b = a
a = “Goodbye”

puts a
puts b
```

### Example 2
What does the following code return? What does it output? Why? What concept does it demonstrate?

```ruby
a = 4

loop do
  a = 5
  b = 3
  break
end

puts a
puts b
```

### Example 3
What does the following code return? What does it output? Why? What concept does it demonstrate?

```ruby
a = 4
b = 2

loop do
  c = 3
  a = c
  break
end

puts a
puts b
```

### Example 4
What does the following code return? What does it output? Why? What concept does it demonstrate?

```Ruby
def example(str)
  i = 3
  loop do
    puts str
    i -= 1
    break if i == 0
    end
end

example('hello')
```

### Example 5
What does the following code return? What does it output? Why? What concept does it demonstrate?

```ruby
def greetings(str)
  puts str
  puts "Goodbye"
end

word = "Hello"
greetings(word)
```

### Example 6
What does the following code return? What does it output? Why? What concept does it demonstrate?

```ruby
arr = [1, 2, 3, 4]
counter = 0
sum = 0

loop do
  sum += arr[counter]
  counter += 1
  break if counter == arr.size
end

puts "Your total is #{sum}"
```

### Example 7
What does the following code return? What does it output? Why? What concept does it demonstrate?

```ruby
a = 'Bob'
5.times do |x|
  a = 'Bill'
end

p a
```

### Example 8
What does the following code return? What does it output? Why? What concept does it demonstrate?

```ruby
animal = "dog"

loop do |_|
  animal = "cat"
  var = "ball"
  break
end

puts animal
puts var
```

## Variable Shadowing
### Example 1
What does the following code return? What does it output? Why? What concept does it demonstrate?

```ruby
animal = "dog"
loop do |_|
  animal = "cat"
  var = "ball"
  break
end

puts animal
puts var
```

### Example 2
What does the following code return? What does it output? Why? What concept does it demonstrate?

```ruby
a = 4
b = 22.times do |a| 
      a = 5 
      puts a
    end

puts a
puts b
```

### Example 3
What does the following code return? What does it output? Why? What concept does it demonstrate?

```ruby
n = 101.times do |n| 
      n = 11
    end

puts n
```

### Example 4
What does the following code return? What does it output? Why? What concept does it demonstrate?

```ruby
animal = "dog"

loop do |animal|
  animal = "cat"
  break
end

puts animal
```

## Object Passing/Variables As Pointers
Link to article on Object Passing:
https://launchschool.medium.com/object-passing-in-ruby-pass-by-reference-or-pass-by-value-6886e8cdc34a
### Example 1
What does the following code return? What does it output? Why? What concept does it demonstrate?

```ruby
a = "hi there"
b = a
a = "not here"

p a
p b
```

What are `a` and `b`?

### Example 2
What does the following code return? What does it output? Why? What concept does it demonstrate?

```ruby
a = "hi there"
b = a
a << ", Bob"

p a
p b
```

What are `a` and `b`?

### Example 3
What does the following code return? What does it output? Why? What concept does it demonstrate?

```ruby
a = [1, 2, 3, 3]
b = a
c = a.uniq

p a
p b
p c
```

What are `a`, `b`, and `c`? What if the last line was `c = a.uniq!`?

### Example 4
What does the following code return? What does it output? Why? What concept does it demonstrate?

```ruby
def test(b) 
  b.map { |letter| "I like the letter: #{letter}" } 
end

a = ['a', 'b', 'c']

p test(a)

p a
```

What is `a`? What if we called `map!` instead of `map`?

### Example 5
What does the following code return? What does it output? Why? What concept does it demonstrate?

```ruby
a = 5.2
b = 7.3
a = b
b += 1.1
  
p a
p b
```

What is `a` and `b`? Why?

### Example 6
What does the following code return? What does it output? Why? What concept does it demonstrate?

```ruby
def test(str)
  str += '!'
  str.downcase!
end

test_str = 'Written Assessment'

test(test_str)
puts test_str
```

### Example 7
What does the following code return? What does it output? Why? What concept does it demonstrate?

```ruby
def plus(x, y)
  x = x + y
end

a = 3
b = plus(a, 2)

puts a
puts b
```

### Example 8
What does the following code return? What does it output? Why? What concept does it demonstrate?

```ruby
def increment(x)
  x << 'b'
end

y = 'a'

increment(y)
puts y
```

### Example 9
What does the following code return? What does it output? Why? What concept does it demonstrate?

```ruby
def change_name(name)
  name = 'bob'
end 

name = 'jim'

change_name(name)
puts name
```

Does this reassignment change the object outside the method?

### Example 10
What does the following code return? What does it output? Why? What concept does it demonstrate?

```ruby
def cap(str)
  str.capitalize!
end

name = "jim"

cap(name)
puts name
```

Does this affect the object outside the method?
### Example 11
What is `arr`? Why? What concept does it demonstrate?

```ruby
a = [1, 3]
b = [2]
arr = [a, b]
arra[1] = 5arr
```

### Example 12

```ruby
arr1 = ["a", "b", "c"]
arr2 = arr1.dup
arr2.map! do |char| 
  char.upcase
end

puts arr1
puts arr2
```

## Object Mutability/Mutating Methods
Article on Mutating and Non-Mutating Methods:
https://launchschool.medium.com/ruby-objects-mutating-and-non-mutating-methods-78023d849a5f
### Example 1
What does the following code return? What does it output? Why? What concept does it demonstrate?

```ruby
def fix(value)
  value.upcase!
  value.concat('!')
  value
end

s = 'hello'
t = fix(s)
```

What values do `s` and `t` have? Why?

### Example 2
What does the following code return? What does it output? Why? What concept does it demonstrate?

```ruby
def fix(value)
  value = value.upcase
  value.concat('!')
end

s = 'hello'
t = fix(s)
```

What values do `s` and `t` have? Why?

### Example 3
What does the following code return? What does it output? Why? What concept does it demonstrate?

```ruby
def fix(value)
  value << 'xyz'
  value = value.upcase
  value.concat('!')
end

s = 'hello'
t = fix(s)
```

What values do `s` and `t` have? Why?

### Example 4
What does the following code return? What does it output? Why? What concept does it demonstrate?

```ruby
def fix(value)
  value = value.upcase!
  value.concat('!')
end

s = 'hello'
t = fix(s)
```

What values do `s` and `t` have? Why?

### Example 5
What does the following code return? What does it output? Why? What concept does it demonstrate?
```ruby
def fix(value)
  value[1] = 'x'
  value
end

s = 'abc'
t = fix(s)
```

What values do `s` and `t` have? Why?

### Example 6
What does the following code return? What does it output? Why? What concept does it demonstrate?

```ruby
def a_method(string)
  string << ' world'
end

a = 'hello'

a_method(a)
p a
```

### Example 7
What does the following code return? What does it output? Why? What concept does it demonstrate?

```ruby
num = 3
num = 2 * num
```

### Example 8
What does the following code return? What does it output? Why? What concept does it demonstrate?

```ruby
a = %w(a b c)
a[1] = '-'

p a
```

### Example 9

```ruby
def add_name(arr, name)
  arr = arr + [name]
end

names = ['bob', 'kim']
add_name(names, 'jim')

puts names
```

### Example 10

```ruby

def add_name(arr, name)
  arr = arr << name
end

names = ['bob', 'kim']
add_name(names, 'jim')

puts names
```


## Truthiness
### Example 1
What does the following code return? What does it output? Why? What concept does it demonstrate?

```ruby
a = "Hello"

if a 
  puts "Hello is truthy"
else
  puts "Hello is falsey"
end
```

### Example 2
What does the following code return? What does it output? Why? What concept does it demonstrate?

```ruby
def test
  puts "written assessment"
end

var = test

if var 
  puts "written assessment"
else 
  puts "interview"
end
```