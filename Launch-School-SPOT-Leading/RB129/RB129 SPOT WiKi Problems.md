# 1.

|   |
|---|
|class Person  <br>  attr_reader :name  <br>   <br>  def set_name  <br>    @name = 'Bob'  <br>  end  <br>end  <br>  <br>bob = Person.new  <br>p bob.name|

  

# What is output and why? What does this demonstrate about instance variables that differentiates them from local variables?

  

# 2.

|   |
|---|
|module Swimmable  <br>  def enable_swimming  <br>    @can_swim = true  <br>  end  <br>end  <br>  <br>class Dog  <br>  include Swimmable  <br>  <br>  def swim  <br>    "swimming!" if @can_swim  <br>  end  <br>end  <br>  <br>teddy = Dog.new  <br>p teddy.swim|

  

# What is output and why? What does this demonstrate about instance variables?

  

# 3. 

|   |
|---|
|module Describable  <br>  def describe_shape  <br>    "I am a #{self.class} and have #{SIDES} sides."  <br>  end  <br>end  <br>  <br>class Shape  <br>  include Describable  <br>  <br>  def self.sides  <br>    self::SIDES  <br>  end  <br>   <br>  def sides  <br>    self.class::SIDES  <br>  end  <br>end  <br>  <br>class Quadrilateral < Shape  <br>  SIDES = 4  <br>end  <br>  <br>class Square < Quadrilateral; end  <br>  <br>p Square.sides  <br>p Square.new.sides  <br>p Square.new.describe_shape|

  

# What is output and why? What does this demonstrate about constant scope? What does `self` refer to in each of the 3 methods above? 

  

# 4.

|   |
|---|
|class AnimalClass  <br>  attr_accessor :name, :animals  <br>   <br>  def initialize(name)  <br>    @name = name  <br>    @animals = []  <br>  end  <br>   <br>  def <<(animal)  <br>    animals << animal  <br>  end  <br>   <br>  def +(other_class)  <br>    animals + other_class.animals  <br>  end  <br>end  <br>  <br>class Animal  <br>  attr_reader :name  <br>   <br>  def initialize(name)  <br>    @name = name  <br>  end  <br>end  <br>  <br>mammals = AnimalClass.new('Mammals')  <br>mammals << Animal.new('Human')  <br>mammals << Animal.new('Dog')  <br>mammals << Animal.new('Cat')  <br>  <br>birds = AnimalClass.new('Birds')  <br>birds << Animal.new('Eagle')  <br>birds << Animal.new('Blue Jay')  <br>birds << Animal.new('Penguin')  <br>  <br>some_animal_classes = mammals + birds  <br>  <br>p some_animal_classes|

  

# What is output? Is this what we would expect when using `AnimalClass#+`? If not, how could we adjust the implementation of `AnimalClass#+` to be more in line with what we'd expect the method to return?

  
  

# 5.

|                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| class GoodDog  <br>  attr_accessor :name, :height, :weight  <br>  <br>  def initialize(n, h, w)  <br>    @name = n  <br>    @height = h  <br>    @weight = w  <br>  end  <br>  <br>  def change_info(n, h, w)  <br>    name = n  <br>    height = h  <br>    weight = w  <br>  end  <br>  <br>  def info  <br>    "#{name} weighs #{weight} and is #{height} tall."  <br>  end  <br>end  <br>  <br>  <br>sparky = GoodDog.new('Spartacus', '12 inches', '10 lbs')  <br>sparky.change_info('Spartacus', '24 inches', '45 lbs')  <br>puts sparky.info  <br># => Spartacus weighs 10 lbs and is 12 inches tall. |

  

# We expect the code above to output `”Spartacus weighs 45 lbs and is 24 inches tall.”` Why does our `change_info` method not work as expected?

# 6.

|   |
|---|
|class Person  <br>  attr_accessor :name  <br>  <br>  def initialize(name)  <br>    @name = name  <br>  end  <br>   <br>  def change_name  <br>    name = name.upcase  <br>  end  <br>end  <br>  <br>bob = Person.new('Bob')  <br>p bob.name  <br>bob.change_name  <br>p bob.name|

  

# In the code above, we hope to output `'BOB'` on `line 16`. Instead, we raise an error. Why? How could we adjust this code to output `'BOB'`? 

  

# 7.

|   |
|---|
|class Vehicle  <br>  @@wheels = 4  <br>  <br>  def self.wheels  <br>    @@wheels  <br>  end  <br>end  <br>  <br>p Vehicle.wheels                              <br>  <br>class Motorcycle < Vehicle  <br>  @@wheels = 2  <br>end  <br>  <br>p Motorcycle.wheels                            <br>p Vehicle.wheels                               <br>  <br>class Car < Vehicle; end  <br>  <br>p Vehicle.wheels  <br>p Motorcycle.wheels                            <br>p Car.wheels|

  

# What does the code above output, and why? What does this demonstrate about class variables, and why we should avoid using class variables when working with inheritance?

  

# 8.

|   |
|---|
|class Animal  <br>  attr_accessor :name  <br>  <br>  def initialize(name)  <br>    @name = name  <br>  end  <br>end  <br>  <br>class GoodDog < Animal  <br>  def initialize(color)  <br>    super  <br>    @color = color  <br>  end  <br>end  <br>  <br>bruno = GoodDog.new("brown")        <br>p bruno|

  

# What is output and why? What does this demonstrate about `super`?

  

# 9.

|   |
|---|
|class Animal  <br>  def initialize  <br>  end  <br>end  <br>  <br>class Bear < Animal  <br>  def initialize(color)  <br>    super  <br>    @color = color  <br>  end  <br>end  <br>  <br>bear = Bear.new("black")|

  

# What is output and why? What does this demonstrate about `super`? 

  

# 10.

|   |
|---|
|module Walkable  <br>  def walk  <br>    "I'm walking."  <br>  end  <br>end  <br>  <br>module Swimmable  <br>  def swim  <br>    "I'm swimming."  <br>  end  <br>end  <br>  <br>module Climbable  <br>  def climb  <br>    "I'm climbing."  <br>  end  <br>end  <br>  <br>module Danceable  <br>  def dance  <br>    "I'm dancing."  <br>  end  <br>end  <br>  <br>class Animal  <br>  include Walkable  <br>  <br>  def speak  <br>    "I'm an animal, and I speak!"  <br>  end  <br>end  <br>  <br>module GoodAnimals  <br>  include Climbable  <br>  <br>  class GoodDog < Animal  <br>    include Swimmable  <br>    include Danceable  <br>  end  <br>   <br>  class GoodCat < Animal; end  <br>end  <br>  <br>good_dog = GoodAnimals::GoodDog.new  <br>p good_dog.walk|

  

# What is the method lookup path used when invoking `#walk` on `good_dog`?

  

# 11.

|   |
|---|
|class Animal  <br>  def eat  <br>    puts "I eat."  <br>  end  <br>end  <br>  <br>class Fish < Animal  <br>  def eat  <br>    puts "I eat plankton."  <br>  end  <br>end  <br>  <br>class Dog < Animal  <br>  def eat  <br>    puts "I eat kibble."  <br>  end  <br>end  <br>  <br>def feed_animal(animal)  <br>  animal.eat  <br>end  <br>  <br>array_of_animals = [Animal.new, Fish.new, Dog.new]  <br>array_of_animals.each do \|animal\|  <br>  feed_animal(animal)  <br>end|

  

# What is output and why? How does this code demonstrate polymorphism? 

# 12.

|   |
|---|
|class Person  <br>  attr_accessor :name, :pets  <br>  <br>  def initialize(name)  <br>    @name = name  <br>    @pets = []  <br>  end  <br>end  <br>  <br>class Pet  <br>  def jump  <br>    puts "I'm jumping!"  <br>  end  <br>end  <br>  <br>class Cat < Pet; end  <br>  <br>class Bulldog < Pet; end  <br>  <br>bob = Person.new("Robert")  <br>  <br>kitty = Cat.new  <br>bud = Bulldog.new  <br>  <br>bob.pets << kitty  <br>bob.pets << bud                      <br>  <br>bob.pets.jump|

  

# We raise an error in the code above. Why? What do `kitty` and `bud` represent in relation to our `Person` object?  

  

# 13.

|   |
|---|
|class Animal  <br>  def initialize(name)  <br>    @name = name  <br>  end  <br>end  <br>  <br>class Dog < Animal  <br>  def initialize(name); end  <br>  <br>  def dog_name  <br>    "bark! bark! #{@name} bark! bark!"  <br>  end  <br>end  <br>  <br>teddy = Dog.new("Teddy")  <br>puts teddy.dog_name|

  

# What is output and why?

  

# 14.

|   |
|---|
|class Person  <br>  attr_reader :name  <br>  <br>  def initialize(name)  <br>    @name = name  <br>  end  <br>end  <br>  <br>al = Person.new('Alexander')  <br>alex = Person.new('Alexander')  <br>p al == alex # => true|

  

# In the code above, we want to compare whether the two objects have the same name. `Line 11` currently returns `false`. How could we return `true` on `line 11`? 

  

# Further, since `al.name == alex.name` returns `true`, does this mean the `String` objects referenced by `al` and `alex`'s `@name` instance variables are the same object? How could we prove our case?

  
  

# 15.

|   |
|---|
|class Person  <br>  attr_reader :name  <br>  <br>  def initialize(name)  <br>    @name = name  <br>  end  <br>  <br>  def to_s  <br>    "My name is #{name.upcase!}."  <br>  end  <br>end  <br>  <br>bob = Person.new('Bob')  <br>puts bob.name  <br>puts bob  <br>puts bob.name|

  

# What is output on `lines 14, 15, and 16` and why?

  

#  16.

# Why is it generally safer to invoke a setter method (if available) vs. referencing the instance variable directly when trying to set an instance variable within the class? Give an example.

  

# 17.

# Give an example of when it would make sense to manually write a custom getter method vs. using `attr_reader`.

# 18. 

|   |
|---|
|class Shape  <br>  @@sides = nil  <br>  <br>  def self.sides  <br>    @@sides  <br>  end  <br>  <br>  def sides  <br>    @@sides  <br>  end  <br>end  <br>  <br>class Triangle < Shape  <br>  def initialize  <br>    @@sides = 3  <br>  end  <br>end  <br>  <br>class Quadrilateral < Shape  <br>  def initialize  <br>    @@sides = 4  <br>  end  <br>end|

  

# What can executing `Triangle.sides` return? What can executing `Triangle.new.sides` return? What does this demonstrate about class variables?

  

# 19.

# What is the `attr_accessor` method, and why wouldn’t we want to just add `attr_accessor` methods for every instance variable in our class? Give an example.

# 20.

# What is the difference between states and behaviors?

# 21. 

# What is the difference between instance methods and class methods?

# 22.

# What are collaborator objects, and what is the purpose of using them in OOP? Give an example of how we would work with one.

# 23.

# How and why would we implement a fake operator in a custom class? Give an example.

# 24.

# What are the use cases for `self` in Ruby, and how does `self` change based on the scope it is used in? Provide examples.

# 25.

|   |
|---|
|class Person  <br>  def initialize(n)  <br>    @name = n  <br>  end  <br>   <br>  def get_name  <br>    @name  <br>  end  <br>end  <br>  <br>bob = Person.new('bob')  <br>joe = Person.new('joe')  <br>  <br>puts bob.inspect # => #<Person:0x000055e79be5dea8 @name="bob">  <br>puts joe.inspect # => #<Person:0x000055e79be5de58 @name="joe">  <br>  <br>p bob.get_name # => "bob"|

  

 # What does the above code demonstrate about how instance variables are scoped?

  

# 26.

# How do class inheritance and mixing in modules affect instance variable scope? Give an example.

# 27.

# How does encapsulation relate to the public interface of a class?

  

# 28.

|   |
|---|
|class GoodDog  <br>  DOG_YEARS = 7  <br>  <br>  attr_accessor :name, :age  <br>  <br>  def initialize(n, a)  <br>    self.name = n  <br>    self.age  = a * DOG_YEARS  <br>  end  <br>end  <br>  <br>sparky = GoodDog.new("Sparky", 4)  <br>puts sparky|

  

# What is output and why? How could we output a message of our choice instead?

  

# How is the output above different than the output of the code below, and why?

  

|   |
|---|
|class GoodDog  <br>  DOG_YEARS = 7  <br>  <br>  attr_accessor :name, :age  <br>  <br>  def initialize(n, a)  <br>    @name = n  <br>    @age  = a * DOG_YEARS  <br>  end  <br>end  <br>  <br>sparky = GoodDog.new("Sparky", 4)  <br>p sparky|

  

# 29.

# When does accidental method overriding occur, and why? Give an example.

# 30.

# How is Method Access Control implemented in Ruby? Provide examples of when we would use public, protected, and private access modifiers.

# 31.

# Describe the distinction between modules and classes.

# 32.

# What is polymorphism and how can we implement polymorphism in Ruby? Provide examples.

# 33.

# What is encapsulation, and why is it important in Ruby? Give an example.

# 34.

|   |
|---|
|module Walkable  <br>  def walk  <br>    "#{name} #{gait} forward"  <br>  end  <br>end  <br>  <br>class Person  <br>  include Walkable  <br>  <br>  attr_reader :name  <br>  <br>  def initialize(name)  <br>    @name = name  <br>  end  <br>  <br>  private  <br>  <br>  def gait  <br>    "strolls"  <br>  end  <br>end  <br>  <br>class Cat  <br>  include Walkable  <br>  <br>  attr_reader :name  <br>  <br>  def initialize(name)  <br>    @name = name  <br>  end  <br>  <br>  private  <br>  <br>  def gait  <br>    "saunters"  <br>  end  <br>end  <br>  <br>mike = Person.new("Mike")  <br>p mike.walk  <br>  <br>kitty = Cat.new("Kitty")  <br>p kitty.walk|

  

# What is returned/output in the code? Why did it make more sense to use a module as a mixin vs. defining a parent class and using class inheritance?

# 35.

# What is Object Oriented Programming, and why was it created? What are the benefits of OOP, and examples of problems it solves?

  

# 36.

# What is the relationship between classes and objects in Ruby?

# 37.

# When should we use class inheritance vs. interface inheritance?

# 38.

|   |
|---|
|class Cat  <br>end  <br>  <br>whiskers = Cat.new  <br>ginger = Cat.new  <br>paws = Cat.new|

  

# If we use `==` to compare the individual `Cat` objects in the code above, will the return value be `true`? Why or why not? What does this demonstrate about classes and objects in Ruby, as well as the `==` method?

# 39.

|   |
|---|
|class Thing  <br>end  <br>  <br>class AnotherThing < Thing  <br>end  <br>  <br>class SomethingElse < AnotherThing  <br>end|

  

# Describe the inheritance structure in the code above, and identify all the superclasses.

# 40.

|   |
|---|
|module Flight  <br>  def fly; end  <br>end  <br>  <br>module Aquatic  <br>  def swim; end  <br>end  <br>  <br>module Migratory  <br>  def migrate; end  <br>end  <br>  <br>class Animal  <br>end  <br>  <br>class Bird < Animal  <br>end  <br>  <br>class Penguin < Bird  <br>  include Aquatic  <br>  include Migratory  <br>end  <br>  <br>pingu = Penguin.new  <br>pingu.fly|

  

What is the method lookup path that Ruby will use as a result of the call to the `fly` method? Explain how we can verify this.

# 41.

|   |
|---|
|class Animal  <br>  def initialize(name)  <br>    @name = name  <br>  end  <br>  <br>  def speak  <br>    puts sound  <br>  end  <br>  <br>  def sound  <br>    "#{@name} says "  <br>  end  <br>end  <br>  <br>class Cow < Animal  <br>  def sound  <br>    super + "moooooooooooo!"  <br>  end  <br>end  <br>  <br>daisy = Cow.new("Daisy")  <br>daisy.speak|

  

# What does this code output and why?

  

# 42.

|   |
|---|
|class Cat  <br>  def initialize(name, coloring)  <br>    @name = name  <br>    @coloring = coloring  <br>  end  <br>  <br>  def purr; end  <br>  <br>  def jump; end  <br>  <br>  def sleep; end  <br>  <br>  def eat; end  <br>end  <br>  <br>max = Cat.new("Max", "tabby")  <br>molly = Cat.new("Molly", "gray")|

  

# Do `molly` and `max` have the same states and behaviors in the code above? Explain why or why not, and what this demonstrates about objects in Ruby.

  

# 43.

|   |
|---|
|class Student  <br>  attr_accessor :name, :grade  <br>  <br>  def initialize(name)  <br>    @name = name  <br>    @grade = nil  <br>  end  <br>   <br>  def change_grade(new_grade)  <br>    grade = new_grade  <br>  end  <br>end  <br>  <br>priya = Student.new("Priya")  <br>priya.change_grade('A')  <br>priya.grade|

  

# In the above code snippet, we want to return `”A”`. What is actually returned and why? How could we adjust the code to produce the desired result?

# 44.

|   |
|---|
|class MeMyselfAndI  <br>  self  <br>  <br>  def self.me  <br>    self  <br>  end  <br>  <br>  def myself  <br>    self  <br>  end  <br>end  <br>  <br>i = MeMyselfAndI.new|

  

# What does each `self` refer to in the above code snippet?

  

# 45.

|   |
|---|
|class Student  <br>  attr_accessor :grade  <br>  <br>  def initialize(name, grade=nil)  <br>    @name = name  <br>  end  <br>end  <br>  <br>ade = Student.new('Adewale')  <br>p ade # => #<Student:0x00000002a88ef8 @grade=nil, @name="Adewale">|

  

# Running the following code will not produce the output shown on the last line. Why not? What would we need to change, and what does this demonstrate about instance variables?

# 46.

|   |
|---|
|class Character  <br>  attr_accessor :name  <br>  <br>  def initialize(name)  <br>    @name = name  <br>  end  <br>  <br>  def speak  <br>    "#{@name} is speaking."  <br>  end  <br>end  <br>  <br>class Knight < Character  <br>  def name  <br>    "Sir " + super  <br>  end  <br>end  <br>  <br>sir_gallant = Knight.new("Gallant")  <br>p sir_gallant.name  <br>p sir_gallant.speak|

  

# What is output and returned, and why? What would we need to change so that the last line outputs `”Sir Gallant is speaking.”`? 

  

# 47. 

|   |
|---|
|class FarmAnimal  <br>  def speak  <br>    "#{self} says "  <br>  end  <br>end  <br>  <br>class Sheep < FarmAnimal  <br>  def speak  <br>    super + "baa!"  <br>  end  <br>end  <br>  <br>class Lamb < Sheep  <br>  def speak  <br>    super + "baaaaaaa!"  <br>  end  <br>end  <br>  <br>class Cow < FarmAnimal  <br>  def speak  <br>    super + "mooooooo!"  <br>  end  <br>end  <br>  <br>p Sheep.new.speak  <br>p Lamb.new.speak  <br>p Cow.new.speak|

  

# What is output and why? 

# 48.

|   |
|---|
|class Person  <br>  def initialize(name)  <br>    @name = name  <br>  end  <br>end  <br>  <br>class Cat  <br>  def initialize(name, owner)  <br>    @name = name  <br>    @owner = owner  <br>  end  <br>end  <br>  <br>sara = Person.new("Sara")  <br>fluffy = Cat.new("Fluffy", sara)|

  

# What are the collaborator objects in the above code snippet, and what makes them collaborator objects?

# 49.

|   |
|---|
|number = 42  <br>  <br>case number  <br>when 1          then 'first'  <br>when 10, 20, 30 then 'second'  <br>when 40..49     then 'third'  <br>end|

  

# What methods does this `case` statement use to determine which `when` clause is executed?

  

# 50.

|   |
|---|
|class Person  <br>  TITLES = ['Mr', 'Mrs', 'Ms', 'Dr']  <br>  <br>  @@total_people = 0  <br>  <br>  def initialize(name)  <br>    @name = name  <br>  end  <br>  <br>  def age  <br>    @age  <br>  end  <br>end|

# What are the scopes of each of the different variables in the above code?

# 51.

# The following is a short description of an application that lets a customer place an order for a meal:

  

# - A meal always has three meal items: a burger, a side, and drink.

# - For each meal item, the customer must choose an option.

# - The application must compute the total cost of the order.

  

# 1. Identify the nouns and verbs we need in order to model our classes and methods.

# 2. Create an outline in code (a spike) of the structure of this application.

# 3. Place methods in the appropriate classes to correspond with various verbs.

  

# 52. 

|   |
|---|
|class Cat  <br>  attr_accessor :type, :age  <br>  <br>  def initialize(type)  <br>    @type = type  <br>    @age  = 0  <br>  end  <br>  <br>  def make_one_year_older  <br>    self.age += 1  <br>  end  <br>end|

  

# In the `make_one_year_older` method we have used `self`. What is another way we could write this method so we don't have to use the `self` prefix? Which use case would be preferred according to best practices in Ruby, and why?

# 53.

|   |
|---|
|module Drivable  <br>  def self.drive  <br>  end  <br>end  <br>  <br>class Car  <br>  include Drivable  <br>end  <br>  <br>bobs_car = Car.new  <br>bobs_car.drive|

  

# What is output and why? What does this demonstrate about how methods need to be defined in modules, and why?

# 54.

|   |
|---|
|class House  <br>  attr_reader :price  <br>  <br>  def initialize(price)  <br>    @price = price  <br>  end  <br>end  <br>  <br>home1 = House.new(100_000)  <br>home2 = House.new(150_000)  <br>puts "Home 1 is cheaper" if home1 < home2 # => Home 1 is cheaper  <br>puts "Home 2 is more expensive" if home2 > home1 # => Home 2 is more expensive|

  

# What module/method could we add to the above code snippet to output the desired output on the last 2 lines, and why?

  
  
  
  
**