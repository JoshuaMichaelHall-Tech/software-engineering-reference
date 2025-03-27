**stack trace**
2.2.1 :027 > post.categories << news
   (0.1ms)  begin transaction
  SQL (0.5ms)  INSERT INTO "post_categories" ("category_id", "post_id") VALUES (?, ?)  [["category_id", 3], ["post_id", 6]]
   (1.9ms)  rollback transaction
NoMethodError: undefined method `name' for nil:NilClass
    from /Users/jim/.rvm/gems/ruby-2.2.1/gems/activerecord-4.0.0/lib/active_record/associations/has_many_association.rb:80:in `cached_counter_attribute_name'
    from /Users/jim/.rvm/gems/ruby-2.2.1/gems/activerecord-4.0.0/lib/active_record/associations/has_many_association.rb:76:in `has_cached_counter?'
    from /Users/jim/.rvm/gems/ruby-2.2.1/gems/activerecord-4.0.0/lib/active_record/associations/has_many_association.rb:84:in `update_counter'
    from /Users/jim/.rvm/gems/ruby-2.2.1/gems/activerecord-4.0.0/lib/active_record/associations/has_many_through_association.rb:66:in `insert_record'
    from /Users/jim/.rvm/gems/ruby-2.2.1/gems/activerecord-4.0.0/lib/active_record/associations/collection_association.rb:523:in `block (2 levels) in concat_records'
    from /Users/jim/.rvm/gems/ruby-2.2.1/gems/activerecord-4.0.0/lib/active_record/associations/collection_association.rb:367:in `add_to_target'
    from /Users/jim/.rvm/gems/ruby-2.2.1/gems/activerecord-4.0.0/lib/active_record/associations/collection_association.rb:522:in `block in concat_records'
    from /Users/jim/.rvm/gems/ruby-2.2.1/gems/activerecord-4.0.0/lib/active_record/associations/collection_association.rb:520:in `each'
    from /Users/jim/.rvm/gems/ruby-2.2.1/gems/activerecord-4.0.0/lib/active_record/associations/collection_association.rb:520:in `concat_records'
    from /Users/jim/.rvm/gems/ruby-2.2.1/gems/activerecord-4.0.0/lib/active_record/associations/has_many_through_association.rb:43:in `concat_records'
    from /Users/jim/.rvm/gems/ruby-2.2.1/gems/activerecord-4.0.0/lib/active_record/associations/collection_association.rb:137:in `block in concat'
    from /Users/jim/.rvm/gems/ruby-2.2.1/gems/activerecord-4.0.0/lib/active_record/associations/collection_association.rb:152:in `block in transaction'
    from /Users/jim/.rvm/gems/ruby-2.2.1/gems/activerecord-4.0.0/lib/active_record/connection_adapters/abstract/database_statements.rb:202:in `block in transaction'
    from /Users/jim/.rvm/gems/ruby-2.2.1/gems/activerecord-4.0.0/lib/active_record/connection_adapters/abstract/database_statements.rb:210:in `within_new_transaction'
    from /Users/jim/.rvm/gems/ruby-2.2.1/gems/activerecord-4.0.0/lib/active_record/connection_adapters/abstract/database_statements.rb:202:in `transaction'
    from /Users/jim/.rvm/gems/ruby-2.2.1/gems/activerecord-4.0.0/lib/active_record/transactions.rb:209:in `transaction'
    from /Users/jim/.rvm/gems/ruby-2.2.1/gems/activerecord-4.0.0/lib/active_record/associations/collection_association.rb:151:in `transaction'
    from /Users/jim/.rvm/gems/ruby-2.2.1/gems/activerecord-4.0.0/lib/active_record/associations/collection_association.rb:137:in `concat'
    from /Users/jim/.rvm/gems/ruby-2.2.1/gems/activerecord-4.0.0/lib/active_record/associations/has_many_through_association.rb:37:in `concat'
    from /Users/jim/.rvm/gems/ruby-2.2.1/gems/activerecord-4.0.0/lib/active_record/associations/collection_proxy.rb:945:in `<<'
    from (irb):27
    from /Users/jim/.rvm/gems/ruby-2.2.1/gems/railties-4.0.0/lib/rails/commands/console.rb:90:in `start'
    from /Users/jim/.rvm/gems/ruby-2.2.1/gems/railties-4.0.0/lib/rails/commands/console.rb:9:in `start'
    from /Users/jim/.rvm/gems/ruby-2.2.1/gems/railties-4.0.0/lib/rails/commands.rb:64:in `<top (required)>'
    from bin/rails:4:in `require'
    from bin/rails:4:in `<main>'2.2.1 :028 >

**Resources for [Debugging](https://www.schneems.com/2016/01/25/ruby-debugging-magic-cheat-sheet.html)
1. Search Engine
2. [Stack Overflow](http://stackoverflow.com/)
3. [Ruby Docs](https://docs.ruby-lang.org/en/)

**Steps to Debugging**
1. Reproduce the Error
2. Determine the Boundaries of the Error
	1. modify the data or code to get an idea of the scope of the error and determine the boundaries of the problem.
3. Trace the Code
	1. trapping the error - isolating the problem to a segment of the code
4. Understand the Problem Well
5. Implement a Fix
	1. Suppress the error: ```model.start_with?("M") rescue false # => false``` (Generally not the way to go)
	2. Fix one problem at a time.
6. Test the Fix

**Techniques for Debugging**
1. Line by Line (Read/Understand)
2. [Rubber Duck Debugging](https://en.wikipedia.org/wiki/Rubber_duck_debugging)
3. Walking Away (First load problem in brain)
4. [Pry](https://pry.github.io/)*
5. [Tap](https://www.rubypigeon.com/posts/object-tap-and-how-to-use-it/)

**How to Use Pry**
```Terminal
$ gem install pry
```

```RUBY
require "pry" # add this to use Pry 

counter = 0 
loop do 
  counter += 1 
  binding.pry  # execution will stop here 
  break if counter == 5 
end
```
Pry stops the execution at that point, and you can enter additional commands in the terminal:

```Ctrl + D```  Continues execution of program
```exit-program```  Exits Pry

# Pry Cheat Sheet

- [Youtube Tutorial 2013](https://www.youtube.com/watch?v=D9j_Mf91M0I)

Command Line

- `pry -r ./config/app_init_file.rb` - load your app into a pry session (look at the file loaded by config.ru)
- `pry -r ./config/environment.rb` - load your rails into a pry session

Debugger

- `help ls` -- Display command options for pry command ls
- `ls <Object>` -- Show all of the available methods that can be called by an object
- `_` -- Last eval
- `? <Object>` -- Shows more information (doc) about an object, or method
- `_file_` -- Represent the last file Pry touched
- `wtf?` -- Print the stack trace, same as `_ex_.backtrace`
- `$` -- Show source, shortcut for show-source
- `edit Class` -- Open file in $EDITOR
- `edit Class#instance_method` -- Open file in $EDITOR
- `<ctrl+r>` -- Search history
- `_out_` -- Array of all outputs values, also `_in_`
- `cd <var>` -- Step into an object, change the value of self
- `cd ..` -- Take out of a level
- `binding.pry` -- Breakpoint
- `edit --ex` -- Edit the file where the last exception was thrown
- `.<Shell>` -- Runs the command
- `whereami` -- Print the context where the debugger is stopped
- `whereami 20` -- Print the context 20 lines where the debugger is stopped
- `;` -- Would mute the return output by Ruby
- `play -l` -- Execute the line in the current debugging context

## [](https://gist.github.com/lfender6445/9919357#pry-nav)pry-nav

- `next` -- execute next line
- `step` -- step into next function call
- `continue` -- continue through stack

## [](https://gist.github.com/lfender6445/9919357#pry-rescue)pry-rescue

- `rescue rspec` -- break on exception in rspec
- `rescue rails server` -- break on exception in rails server
- `try-again` -- run last failing spec, reloads the file not the enviornment

## tap

```Ruby
(1..10) .tap { |x| p x } # 1..10
.to_a .tap { |x| p x } # [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
.select {|x| x.even? } .tap { |x| p x } # [2, 4, 6, 8, 10]
.map {|x| x*x } .tap { |x| p x } # [4, 16, 36, 64, 100]
```

