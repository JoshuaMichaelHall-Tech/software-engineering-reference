```none
$ gem install pry
```

```ruby
require "pry" # add this to use Pry

counter = 0

loop do
  counter += 1
  binding.pry # execution will stop here
  break if counter == 5
end
```

```terminal

From: /Users/temp/count.rb @ line 7 :

    2:
    3: counter = 0
    4:
    5: loop do
    6:   counter += 1
 => 7:   binding.pry # execution will stop here
    8:   break if counter == 5
    9: end

[1] pry(main)> counter
=> 1
[2] pry(main)>
```

```terminal
pry(main)> exit-program
```

**Commands**
gem install pry
require "pry"
binding.pry
exit  (program will continue)
exit-program
CTRL-d continue program
``

