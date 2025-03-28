QUESTIONS (FROM SPOT WIKI)

# RB119 Written Questions - From Christian Larwood's Blog

Edited by Joshua Hall

**Always aim to answer: What does the following code output and return? Why? What concept does it demonstrate?**

## Each, Map, Select
### Example 1
What does the following code return? What does it output? Why? What concept does it demonstrate?

```ruby
array = [1, 2, 3, 4, 5]

array.select do |num|
  puts num if num.odd?
end
```

### Example 2
What does the following code return? What does it output? Why? What concept does it demonstrate?

```ruby
arr = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

arr.select { |n| n.odd? }
```

### Example 3
What does the following code return? What does it output? Why? What concept does it demonstrate?

```ruby
arr = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
new_array = arr.select do |n| 
              n + 1
            end
p new_array
```

### Example 4
What does the following code return? What does it output? Why? What concept does it demonstrate?

```ruby
arr = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
new_array = arr.select do |n|
  n + 1
  puts n
end

p new_array
```

### Example 5
What does the following code return? What does it output? Why? What concept does it demonstrate?

```ruby
words = %w(jump trip laugh run talk)
new_array = words.map do |word|
  word.start_with?("t")
end

p new_array
```

### Example 6
What does the following code return? What does it output? Why? What concept does it demonstrate?

```ruby
arr = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

arr.each { |n| puts n }
```

### Example 7
What does the following code return? What does it output? Why? What concept does it demonstrate?

```ruby
arr = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

incremented = arr.map do |n|
  n + 1
end

p incremented
```

### Example 8
What does the following code return? What does it output? Why? What concept does it demonstrate?

```ruby
arr = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
new_array = arr.map do |n|
  n > 1
end

p new_array
```

### Example 9
What does the following code return? What does it output? Why? What concept does it demonstrate?

```ruby
arr = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
new_array = arr.map do |n|
  n > 1
  puts n
end

p new_array
```

### Example 10
What does the following code return? What does it output? Why? What concept does it demonstrate?

```ruby
a = "hello"[1, 2, 3].map { |num| a }
```

### Example 11
What does the following code return? What does it output? Why? What concept does it demonstrate?

```ruby
[1, 2, 3].each do |num|
  puts num
end
```

## Other Collection Methods
### Example 1

```ruby
[1, 2, 3].any? do |num|
  num > 2
end
```

### Example 2

```ruby
{ a: "ant", b: "bear", c: "cat" }.any? do |key, value|
  value.size > 4
end
```

### Example 3

```ruby
[1, 2, 3].all? do |num|
  num > 2
end
```

### Example 4

```ruby
{ a: "ant", b: "bear", c: "cat" }.all? do |key, value|
  value.length >= 3
end
```

### Example 5

```ruby
[1, 2, 3].each_with_index do |num, index|
  puts "The index of #{num} is #{index}."
end
```

### Example 6

```ruby
{ a: "ant", b: "bear", c: "cat" }.each_with_object([]) do |pair, array|
  array << pair.last
end
```

### Example 7

```ruby
{ a: "ant", b: "bear", c: "cat" }.each_with_object({}) do |(key, value), hash|
  hash[value] = key
end
```

### Example 8

```ruby
odd, even = [1, 2, 3].partition do |num|
  num.odd?
end

p odd
p even
```

