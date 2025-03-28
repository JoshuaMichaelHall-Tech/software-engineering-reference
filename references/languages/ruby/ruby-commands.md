# Ruby Commands Reference

## Basic Ruby Syntax

### Variables and Constants

```ruby
# Variable assignment
name = "John"
age = 30

# Constants (conventionally uppercase)
PI = 3.14159
MAX_USERS = 100

# Parallel assignment
a, b = 10, 20

# Swapping values
a, b = b, a
```

### Data Types

```ruby
# Strings
name = "Ruby"
multiline = "This is a
             multiline string"
interpolation = "Hello, #{name}!"

# Numbers
integer = 42
float = 3.14
complex = 1 + 2i

# Symbols (immutable identifiers)
status = :active
error_code = :"404"

# Arrays
numbers = [1, 2, 3, 4, 5]
mixed = [1, "two", :three, 4.0]
nested = [[1, 2], [3, 4]]

# Hashes
user = { "name" => "John", "age" => 30 }
user_with_symbols = { name: "John", age: 30 }

# Ranges
one_to_ten = 1..10     # Inclusive (1 to 10)
one_to_nine = 1...10   # Exclusive (1 to 9)
```

### Control Flow

```ruby
# If/else statements
if age >= 18
  puts "Adult"
elsif age >= 13
  puts "Teenager"
else
  puts "Child"
end

# One-line conditionals
puts "Adult" if age >= 18

# Unless (inverse of if)
unless age < 18
  puts "Can vote"
end

# Case statement
case status
when :active
  puts "User is active"
when :pending
  puts "User is pending"
else
  puts "Unknown status"
end

# Ternary operator
result = age >= 18 ? "Adult" : "Minor"
```

### Loops and Iteration

```ruby
# Basic loop
loop do
  puts "Infinite loop"
  break if condition
end

# While loop
while count < 10
  puts count
  count += 1
end

# Until loop
until count >= 10
  puts count
  count += 1
end

# For loop
for i in 1..5
  puts i
end

# Each iterator
[1, 2, 3].each do |num|
  puts num
end

# Each with index
["a", "b", "c"].each_with_index do |item, index|
  puts "#{index}: #{item}"
end

# Times iterator
5.times { |i| puts i }

# Map/collect (transformation)
doubled = [1, 2, 3].map { |num| num * 2 }  # => [2, 4, 6]

# Select/filter
evens = [1, 2, 3, 4].select { |num| num.even? }  # => [2, 4]

# Reject
odds = [1, 2, 3, 4].reject { |num| num.even? }  # => [1, 3]
```

## Methods and Blocks

### Method Definition and Calling

```ruby
# Basic method definition
def greet(name)
  "Hello, #{name}!"
end

# Calling methods
greeting = greet("Ruby")

# Default parameters
def greet(name = "World")
  "Hello, #{name}!"
end

# Variable number of arguments
def sum(*numbers)
  numbers.reduce(0, :+)
end

total = sum(1, 2, 3, 4)  # => 10

# Keyword arguments
def create_user(name:, age:, role: "member")
  # Function body
end

user = create_user(name: "John", age: 30)
```

### Blocks, Procs, and Lambdas

```ruby
# Method with a block
def do_twice
  yield if block_given?
  yield if block_given?
end

do_twice { puts "Hello" }

# Explicit block parameter
def with_logging(&block)
  puts "Starting..."
  result = block.call
  puts "Finished!"
  result
end

# Proc objects
my_proc = Proc.new { |x| puts x }
my_proc.call(42)

# Alternative proc creation
my_proc = proc { |x| puts x }

# Lambda creation
my_lambda = lambda { |x| puts x }
my_lambda.call(42)

# Stabby lambda syntax
my_lambda = ->(x) { puts x }

# Symbol to proc shorthand
names = ["john", "paul", "george", "ringo"]
upcased = names.map(&:upcase)  # Same as: names.map { |name| name.upcase }
```

## Classes and Modules

### Class Definition and Instantiation

```ruby
# Basic class
class Person
  def initialize(name, age)
    @name = name
    @age = age
  end
  
  def greet
    "Hello, I'm #{@name}!"
  end
end

# Creating objects
person = Person.new("John", 30)
greeting = person.greet

# Accessors (getters and setters)
class Person
  attr_reader :name       # Creates getter method
  attr_writer :age        # Creates setter method
  attr_accessor :email    # Creates both getter and setter
  
  def initialize(name, age, email)
    @name = name
    @age = age
    @email = email
  end
end

# Class methods
class MathHelper
  def self.square(x)
    x * x
  end
end

result = MathHelper.square(5)  # => 25
```

### Inheritance and Modules

```ruby
# Inheritance
class Animal
  def speak
    "Some sound"
  end
end

class Dog < Animal
  def speak
    "Woof!"
  end
end

# Calling parent methods
class Dog < Animal
  def speak
    super + " Woof!"  # Calls Animal#speak
  end
end

# Module definition
module Loggable
  def log(message)
    puts "[LOG] #{message}"
  end
end

# Mixing in modules
class Product
  include Loggable  # Makes Loggable methods available as instance methods
  
  def save
    log("Product saved!")
  end
end

# Extending modules (adding class methods)
class User
  extend Loggable  # Makes Loggable methods available as class methods
end

User.log("Class method called")
```

### Method Access Control

```ruby
class BankAccount
  def initialize(balance)
    @balance = balance
  end
  
  # Public method (default)
  def display_balance
    "Balance: $#{@balance}"
  end
  
  # Protected methods
  protected
  
  def same_owner?(other_account)
    owner == other_account.owner
  end
  
  # Private methods
  private
  
  def calculate_interest
    @balance * 0.05
  end
end
```

## Collections and Enumerable Methods

### Array Operations

```ruby
# Creating arrays
arr = [1, 2, 3, 4, 5]
arr = Array.new(3, 0)  # => [0, 0, 0]
arr = Array.new(3) { |i| i * 2 }  # => [0, 2, 4]

# Accessing elements
first = arr[0]
last = arr[-1]
slice = arr[1..3]

# Array methods
arr.length    # or arr.size
arr.empty?    # Check if array is empty
arr.include?(3)  # Check if array contains a value
arr.sort      # Sort the array
arr.reverse   # Reverse the array
arr.uniq      # Remove duplicates

# Modifying arrays
arr.push(6)   # Add to end (or arr << 6)
arr.pop       # Remove from end
arr.unshift(0)  # Add to beginning
arr.shift     # Remove from beginning
arr.insert(2, 99)  # Insert at specific position
arr.delete(3)  # Delete specific value
arr.delete_at(2)  # Delete at specific position
```

### Hash Operations

```ruby
# Creating hashes
hash = { "name" => "John", "age" => 30 }
symbol_hash = { name: "John", age: 30 }

# Accessing values
name = hash["name"]
age = symbol_hash[:age]

# Default values
grades = Hash.new(0)  # Default value is 0
grades["Alice"]  # => 0

# Hash methods
hash.keys      # Array of keys
hash.values    # Array of values
hash.length    # Number of key-value pairs
hash.empty?    # Check if hash is empty
hash.include?(:name)  # Check if key exists (or hash.key?(:name))
hash.has_value?("John")  # Check if value exists

# Modifying hashes
hash[:location] = "New York"  # Add or update key-value pair
hash.delete(:age)  # Remove key-value pair
hash.merge!(other_hash)  # Merge with another hash
```

### Enumerable Methods

```ruby
# Each
[1, 2, 3].each { |num| puts num }

# Map/Collect
doubled = [1, 2, 3].map { |num| num * 2 }  # => [2, 4, 6]

# Select/Find_all
evens = [1, 2, 3, 4].select { |num| num.even? }  # => [2, 4]

# Reject
odds = [1, 2, 3, 4].reject { |num| num.even? }  # => [1, 3]

# Find/Detect
first_even = [1, 2, 3, 4].find { |num| num.even? }  # => 2

# Any?
has_even = [1, 2, 3].any? { |num| num.even? }  # => true

# All?
all_positive = [1, 2, 3].all? { |num| num > 0 }  # => true

# None?
no_negatives = [1, 2, 3].none? { |num| num < 0 }  # => true

# Count
even_count = [1, 2, 3, 4].count { |num| num.even? }  # => 2

# Reduce/Inject
sum = [1, 2, 3, 4].reduce(0) { |acc, num| acc + num }  # => 10
product = [1, 2, 3, 4].reduce(1, :*)  # => 24

# Group_by
grouped = [1, 2, 3, 4, 5, 6].group_by { |num| num.even? }
# => {false=>[1, 3, 5], true=>[2, 4, 6]}

# Sort_by
sorted = %w[apple banana pear].sort_by { |fruit| fruit.length }
# => ["pear", "apple", "banana"]

# Each_with_index
[1, 2, 3].each_with_index { |num, idx| puts "#{idx}: #{num}" }

# Each_with_object
result = [1, 2, 3].each_with_object({}) do |num, hash|
  hash[num] = num ** 2
end
# => {1=>1, 2=>4, 3=>9}
```

## File Operations

```ruby
# Reading a file
content = File.read("file.txt")
lines = File.readlines("file.txt")

# Reading a file line by line
File.foreach("file.txt") do |line|
  puts line
end

# Writing to a file
File.write("output.txt", "Hello, world!")

# Appending to a file
File.write("output.txt", "More content", mode: "a")

# Open a file with a block (automatically closes file)
File.open("file.txt", "r") do |file|
  while line = file.gets
    puts line
  end
end

# File information
File.exist?("file.txt")    # Check if file exists
File.directory?("dir")     # Check if it's a directory
File.file?("file.txt")     # Check if it's a file
File.size("file.txt")      # Get file size in bytes
File.basename("/path/to/file.txt")  # => "file.txt"
File.dirname("/path/to/file.txt")   # => "/path/to"
File.extname("file.txt")            # => ".txt"
```

## Exception Handling

```ruby
# Basic exception handling
begin
  # Code that might raise an exception
  result = 10 / 0
rescue ZeroDivisionError => e
  puts "Error: #{e.message}"
end

# Multiple exceptions
begin
  # Code that might raise an exception
rescue ZeroDivisionError => e
  puts "Division error: #{e.message}"
rescue ArgumentError => e
  puts "Argument error: #{e.message}"
rescue => e
  puts "Unknown error: #{e.message}"
end

# Ensure block (always executed)
begin
  file = File.open("file.txt")
  # Process the file
rescue => e
  puts "Error: #{e.message}"
ensure
  file.close if file
end

# Retry
attempts = 0
begin
  # Code that might fail
  raise "Connection error" if attempts < 3
rescue
  attempts += 1
  retry if attempts < 5
  puts "Failed after #{attempts} attempts"
end

# Raising exceptions
def validate_age(age)
  raise ArgumentError, "Age must be positive" if age < 0
  # Continue with validation
end
```

## Testing with Minitest

```ruby
# Basic test
require 'minitest/autorun'

class MyTest < Minitest::Test
  def test_addition
    assert_equal 4, 2 + 2
  end
end

# Common assertions
assert(test)                     # Passes if test is truthy
assert_equal(expected, actual)   # Passes if expected == actual
assert_nil(obj)                  # Passes if obj is nil
assert_raises(exception) { ... } # Passes if the block raises the exception
assert_instance_of(cls, obj)     # Passes if obj is an instance of cls
assert_includes(collection, obj) # Passes if collection includes obj

# Setup and teardown
class ComplexTest < Minitest::Test
  def setup
    @value = 1
    @array = [1, 2, 3]
  end
  
  def test_value
    assert_equal 1, @value
  end
  
  def teardown
    # Clean up resources if needed
  end
end
```

## Debugging

```ruby
# Printing values
puts "Debugging: #{variable}"

# Inspecting objects
p object
pp object  # Pretty print for complex objects

# Using the debugger (with gem 'debug')
require 'debug'
debugger  # Sets a breakpoint

# Using the byebug gem
require 'byebug'
byebug  # Sets a breakpoint

# Using the pry gem
require 'pry'
binding.pry  # Opens a REPL at this point
```

## Gems and Bundler

```ruby
# Installing gems
gem install rails

# Installing specific versions
gem install rails -v 6.1.4

# Gemfile basics
source 'https://rubygems.org'

gem 'rails', '~> 6.1.4'
gem 'pg'

group :development do
  gem 'pry'
end

group :test do
  gem 'rspec'
  gem 'minitest'
end

# Bundler commands
bundle install            # Install all dependencies
bundle update             # Update all gems to latest versions
bundle exec rspec         # Run command with bundle environment
bundle exec rails server  # Run Rails server with bundle environment
```

## Basic Rake Tasks

```ruby
# Rakefile
require 'rake/testtask'

desc 'Run tests'
Rake::TestTask.new do |t|
  t.libs << 'test'
  t.test_files = FileList['test/**/*_test.rb']
  t.verbose = true
end

desc 'Say hello'
task :hello do
  puts "Hello there. This is the `hello` task."
end

desc 'Say goodbye'
task :bye do
  puts 'Bye now!'
end

desc 'Do everything'
task :default => [:hello, :bye, :test]
```

## Sinatra Web Application

```ruby
# Basic Sinatra app
require 'sinatra'
require 'sinatra/reloader' if development?

# Routes
get '/' do
  'Hello, World!'
end

# Route with parameters
get '/hello/:name' do
  "Hello, #{params['name']}!"
end

# Templates with ERB
get '/about' do
  @title = 'About Page'
  erb :about
end

# Sessions
enable :sessions

get '/login' do
  session[:user_id] = params[:id]
  redirect '/'
end

# Forms
post '/users' do
  # Process form submission
  username = params[:username]
  password = params[:password]
  
  # Add user to database
  # ...
  
  redirect '/'
end
```

## Database Operations

```ruby
# Using the pg gem for PostgreSQL
require 'pg'

# Connecting to a database
conn = PG.connect(dbname: 'mydb', user: 'user', password: 'password')

# Executing a query
result = conn.exec('SELECT * FROM users')

# Iterating through results
result.each do |row|
  puts "#{row['id']}: #{row['name']}"
end

# Parameterized queries (prevents SQL injection)
conn.exec_params('SELECT * FROM users WHERE name = $1', ['John'])

# Inserting data
conn.exec_params(
  'INSERT INTO users (name, email) VALUES ($1, $2)',
  ['John', 'john@example.com']
)

# Transaction
conn.transaction do |tx|
  tx.exec('INSERT INTO accounts (id, balance) VALUES (1, 1000)')
  tx.exec('INSERT INTO transactions (account_id, amount) VALUES (1, 1000)')
end

# Closing the connection
conn.close
```

## Regular Expressions

```ruby
# Basic pattern matching
"hello" =~ /ello/   # => 1 (index of match)
"hello" =~ /world/  # => nil (no match)

# Match method
match = "hello".match(/[aeiou]/)
if match
  puts "Found vowel: #{match[0]} at position #{match.begin(0)}"
end

# Common patterns
digits = /\d+/         # One or more digits
word = /\w+/           # One or more word characters
spaces = /\s+/         # One or more whitespace characters
email = /\S+@\S+\.\S+/ # Simple email pattern

# Character classes
vowels = /[aeiou]/     # Any vowel
consonants = /[^aeiou]/  # Any character except vowels

# Quantifiers
zero_or_more = /bo*/     # b followed by zero or more o's
one_or_more = /bo+/      # b followed by one or more o's
zero_or_one = /bo?/      # b followed by zero or one o
exactly_three = /bo{3}/  # b followed by exactly 3 o's
three_to_five = /bo{3,5}/  # b followed by 3 to 5 o's

# Anchors
start_of_string = /^hello/  # String starts with "hello"
end_of_string = /world$/    # String ends with "world"

# Groups and captures
match = "hello world".match(/(\w+)\s+(\w+)/)
first_word = match[1]  # => "hello"
second_word = match[2]  # => "world"

# Substitution
new_string = "hello world".gsub(/[aeiou]/, '*')  # => "h*ll* w*rld"
```
