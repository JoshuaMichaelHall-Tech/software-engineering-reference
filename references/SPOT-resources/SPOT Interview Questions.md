 # By Natalie Thompson
class Person
  def initialize(name, job)
      @name = name
  end 
end

roger = Person.new("Roger", "Carpenter")
puts roger

#Add 1 line of code for the person class
#and 1 line of code in the initalize method. 
#and 1 method containing 1 line.
#Other than that don't change Person.

#Output:
#"My name is Roger and I am a Carpenter"

 # ================================================================

 # By Raul Romero
class Human 
    attr_reader :name

  def initialize(name="Dylan")
    @name = name
  end
  
end

puts Human.new("Jo").hair_colour("blonde")  
#Should output "Hi, my name is Jo and I have blonde hair."

puts Human.hair_colour("")              
#Should output "Hi, my name is Dylan and I have blonde hair."

 # ================================================================

 # By Raul Romero
class Human
  attr_reader :name 
  
  def initialize(name)
  end
 
end

gilles = Human.new("gilles") 
anna = Human.new("gilles") 

puts anna.equal?(gilles) #should output true # 
puts anna + gilles # should output annagilles 

 # HINT: Is it even possible? Why?
 # ================================================================

 # By Joseph Ochoa
 # Describe what the code below outputs and why.

module Attackable
  def attack
    "attacks!"
  end
end

class Characters
  attr_accessor :name, :characters 
  
  def initialize(name) 
    #
    self.name 
    @characters = [] 
  end
  
  def display
    name
  end
  
  protected 
  attr_reader :name
  attr_writer :name
end

class Monster < Characters
  include Attackable
  
  def initialize(name)
    super
  end
end

class Barbarian < Characters
  def ==(other)
    if(super.self == super.self) # 
      super.self == super.self
    end
  end
end

conan = Barbarian.new('barb') 
rob = Monster.new('monst')
conan.characters << rob
p conan.display

 # ================================================================

 # Originally by Joseph Ochoa, edited by Joshua Hall
 # Give class Barbarian the functionality of the Monster instance attack method:

  # Using direct inheritance.

  # Using interface inheritance.

  # Using duck typing.

class Monster
  def attack
    "attacks!"
  end
end

class Barbarian
  
end

 # ================================================================

 # Originally by Natalie Thompson, edited by Oscar Cortes and Joshua Hall
 # Implement a solution:
class ClassA 
  attr_reader :field1, :field2
  
  def initialize(num)
    @field1 = "xyz"
    @field2 = num
  end
end

class ClassB 
  attr_reader :field1

  def initialize
    @field1 = "abc"
  end
end


obj1 = ClassA.new(50)
obj2 = ClassA.new(25)
obj3 = ClassB.new


p obj1 > obj2
p obj2 > obj3

 # ================================================================

 # Anonymous, updated by Joshua Hall
  # Complete the class so the code works.
class BenjaminButton 
  
  def initialize
  end
  
  def get_older
  end
  
  def die
  end
end


benjamin = BenjaminButton.new
p benjamin.actual_age # => 0
p benjamin.appearance_age # => 100

benjamin.actual_age = 1
p benjamin.actual_age

benjamin.get_older
p benjamin.actual_age # => 2
p benjamin.appearance_age # => 99

benjamin.die
p benjamin.actual_age # => 100
p benjamin.appearance_age # => 0

 # ================================================================

 # Originally by Natalie Thompson, Edited by James Wilson
class Wizard
  attr_reader :name, :hitpoints
  
  def initialize(name, hitpoints)
    @name = name
    @hitpoints = hitpoints
  end  
  
  def fireball
    "casts Fireball for 500 damage!"
  end
  
end

class Summoner < Wizard
  attr_reader :souls
  
  def initialize(name, hitpoints)
    # only add one line here
    @souls = []
  end
  
  def soul_steal(character)
    @souls << character
  end
end

gandolf = Summoner.new("Gandolf", 100)
p gandolf.name # => "Gandolf"

valdimar = Wizard.new("Valdimar", 200)
p valdimar.fireball #=> "casts fireball for 500 damage!"

p gandolf.hitpoints #=> 100

p gandolf.soul_steal(valdimar) #=> [#<Wizard:0x000055d782470810 @name="Valdimar", @hitpoints=200>]

p gandolf.souls[0].fireball #=> "casts fireball for 500 damage!"


 # ================================================================

# LS Man...legend says LS Man first appeared in SPOT.
module Flightable
  def fly
  end
end

class Superhero    
  attr_accessor :ability
  
  def self.fight_crime
  end
  
  def initialize(name)
    @name = name
  end
  
  def announce_ability
    puts "I fight crime with my #{ability} ability!"
  end
end

class LSMan < Superhero; end

class Ability
  attr_reader :description

  def initialize(description)
    @description = description
  end
end

superman = Superhero.new('Superman')

p superman.fly # => I am Superman, I am a superhero, and I can fly!

LSMan.fight_crime 
# => I am LSMan!
# => I fight crime with my coding skills ability!

 # ================================================================
