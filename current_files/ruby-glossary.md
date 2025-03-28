# Ruby Programming Master Glossary

## Ruby Language Fundamentals

| Term | Definition |
|------|------------|
| **Block** | Anonymous piece of code that can be passed to methods |
| **Class** | Blueprint for creating objects, defining their attributes and behaviors |
| **Closure** | Chunk of code that can be passed around and retains references to its surrounding scope |
| **Constant** | Variable whose value should not change, written in ALL_CAPS |
| **Enumerable** | Module providing collection iteration methods like `each`, `map`, `select` |
| **Gem** | Packaged Ruby application or library that can be installed and used in your code |
| **Instance Variable** | Variable that exists as long as the object instance exists, prefixed with `@` |
| **Class Variable** | Variable shared among all instances of a class, prefixed with `@@` |
| **Lambda** | Stricter version of a Proc with enforced arity and different return behavior |
| **Method** | Named sequence of statements that performs a specific task |
| **Module** | Container for methods and constants that can be mixed into classes |
| **Object** | Instance of a class with its own state and behaviors |
| **Proc** | Object-oriented version of a block, can be stored in a variable and passed around |
| **Symbol** | Immutable, reusable identifier, prefixed with a colon (`:`) |
| **Yield** | Keyword used within methods to invoke the block passed to that method |

## Object-Oriented Programming Concepts

| Term | Definition |
|------|------------|
| **Abstraction** | Simplifying complex reality by modeling classes based on essential properties |
| **Attribute** | Data item belonging to a class instance, typically implemented as instance variables |
| **Class Method** | Method available to the class itself, defined with `self.method_name` |
| **Constructor** | Special method (`initialize`) that runs when a new object is created |
| **Duck Typing** | Type of polymorphism where an object's suitability is determined by its behavior rather than its class |
| **Encapsulation** | Hiding implementation details and data within objects |
| **Getter Method** | Method that returns the value of an instance variable |
| **Inheritance** | Mechanism for code reuse between classes using the `<` operator |
| **Instance Method** | Method available to objects of a class |
| **Interface** | Set of methods an object responds to |
| **Method Access Control** | Using `public`, `private`, and `protected` keywords to restrict method access |
| **Method Lookup Path** | Order in which Ruby searches for methods in classes and modules |
| **Method Overriding** | Redefining a method in a subclass that was inherited from a superclass |
| **Mixin** | Using modules with `include` to share behavior among unrelated classes |
| **Polymorphism** | Different objects responding to the same interface in different ways |
| **Self** | Keyword that refers to the current object or class depending on context |
| **Setter Method** | Method that sets the value of an instance variable |

## Collections and Iteration

| Term | Definition |
|------|------------|
| **Arity** | Rules about the number of arguments that can be passed to blocks, procs, lambdas, or methods |
| **Array** | Ordered collection of elements with integer indices |
| **Block_given?** | Method to check if a block was provided to a method |
| **Binding** | The surrounding environment/context that a closure retains access to |
| **Explicit Block** | Block converted to a Proc object using the `&` operator in a method parameter |
| **Hash** | Collection of key-value pairs |
| **Implicit Block** | Block passed to a method without being converted to a parameter |
| **Iteration** | Cycling through a collection one element at a time |
| **Method Chaining** | Invoking multiple methods in sequence on the same object |
| **Nested Collection** | Collection containing other collections (arrays within arrays, hashes within arrays, etc.) |
| **Selection** | Filtering a collection based on criteria to create a new collection |
| **Shallow Copy** | Copy that doesn't duplicate nested objects (only the top level collection is copied) |
| **Symbol to Proc** | Converting symbols to procs for iteration using `&:method_name` |
| **Transformation** | Creating a new collection by applying changes to each element of the original |

## Testing and Development

| Term | Definition |
|------|------------|
| **Assertion** | Verification step in testing that confirms expected behavior |
| **Bundler** | Gem dependency manager that ensures consistent environments |
| **Gemfile** | File listing dependencies for a Ruby project |
| **Gemfile.lock** | File that records the exact versions of gems installed by Bundler |
| **Minitest** | Ruby's built-in testing library, comes as a standard gem with Ruby |
| **Rake** | Task automation tool commonly used in Ruby projects |
| **RSpec** | Domain-specific language for testing Ruby code |
| **Test** | Situation or context in which tests are run, containing multiple assertions |
| **Test Suite** | Set of tests for a project, including test cases and helpers |

## Web Development

| Term | Definition |
|------|------------|
| **ERB** | Embedded Ruby, templating system for generating dynamic content |
| **Controller** | Component that processes requests and determines responses |
| **Cookie** | Client-side storage mechanism for maintaining state |
| **Form** | User interface element for submitting data to the server |
| **Flash** | Short-term session storage for messages between requests |
| **Middleware** | Software components that intercept and process requests |
| **Rack** | Interface between Ruby web applications and web servers |
| **Route** | Mapping between URL patterns and application code |
| **Session** | Server-side storage mechanism for maintaining state across requests |
| **Sinatra** | Lightweight Ruby web application framework |
| **Template** | File containing code and markup that gets processed to generate HTML |
| **View** | Template for generating dynamic content |

## Database Concepts

| Term | Definition |
|------|------------|
| **Active Record** | ORM (Object-Relational Mapping) pattern used in Rails |
| **Migration** | Ruby code that creates or modifies database tables and columns |
| **N+1 Query Problem** | Inefficient database access pattern causing multiple queries |
| **ORM** | Object-Relational Mapping, technique to convert between objects and database records |
| **Schema** | Structure that defines the organization of database tables and relationships |
| **Transaction** | Group of database operations that succeed or fail as a unit |
