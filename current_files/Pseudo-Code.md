 Here's an example of some pseudo-code for a method that determines which number is greatest in a collection.

Copy Code

```none
Given a collection of integers.

Iterate through the collection one by one.
  - save the first value as the starting value.
  - for each iteration, compare the saved value with the current value.
  - if the saved value is greater, or it's the same
    - move to the next value in the collection
  - otherwise, if the current value is greater
    - reassign the saved value as the current value

After iterating through the collection, return the saved value.
```

The above is an approach we can take to solve the problem. We don't use programming code first, because we're trying to **load the problem into our brain** first.

**Formal Pseudo-Code**
We'll use the below keywords to assist us, along with their meaning.

|keyword|meaning|
|---|---|
|START|start of the program|
|SET|sets a variable we can use for later|
|GET|retrieve input from user|
|PRINT|displays output to user|
|READ|retrieve value from variable|
|IF / ELSE IF / ELSE|show conditional branches in logic|
|WHILE|show looping logic|
|END|end of the program|START
```
# Given a collection of integers called "numbers"

SET iterator = 1
SET saved_number = value within numbers collection at space 1

WHILE iterator <= length of numbers
  SET current_number = value within numbers collection at space "iterator"
  IF saved_number >= current_number
    go to the next iteration
  ELSE
    saved_number = current_number

  iterator = iterator + 1

PRINT saved_number

END
```
