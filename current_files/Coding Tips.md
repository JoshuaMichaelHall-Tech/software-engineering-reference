1. Name things well
	1. Variables and Methods should be self-explanatory
	2. Use proper conventions
		1. snake_case - for everything except:
		2. PascalCase - for classes
		3. UPPERCASE - for constants
2. Never mutate constants
3. Methods should either return something useful or display something
	1. Return value or side effect, not both
	2. Typically use ! at end when it has side effects
4. Methods should be at same level of abstraction
	1. For example, given the four methods below, which one stands out?
	- `deal()`
	- `hit()`
	- `stay()`
	- `iterate_through_cards()`
5. Method names should reflect mutation
6. Prefix all methods that output values with something like `print_`, `say_` or `display_`.
7. Only one program exit point
8. Know when to use 'do/while' versus 'while' loop
	1. - Here's an example:

Copy Code

```ruby
while answer.downcase != 'n' do
  puts "Continue? (y/n)"
  answer = gets.chomp
end
```

When running this, Ruby will throw an exception of "undefined local variable or method 'answer'". To correct this, we have to initialize answer before the while statement, like this:

Copy Code

```ruby
answer = ''
while answer.downcase != 'n' do
  puts "Continue? (y/n)"
  answer = gets.chomp
end
```

That certainly would work, but a slightly better implementation could be to use a "do/while" loop:

Copy Code

```ruby
loop do
  puts "Continue? (y/n)"
  answer = gets.chomp
  break if answer.downcase == 'n'
end
```

Here, the entire code is contained in the loop, and it's slightly easier to reason with.