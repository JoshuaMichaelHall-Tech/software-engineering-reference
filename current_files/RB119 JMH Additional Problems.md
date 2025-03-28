By Joshua Hall
#### Demonstrate Deep Copy
 
 # Write a recursive method which creates a deep copy of an input array.

def dup_arr(arr)
  # write code here
end

arr1 = ['a', 'b', 'c']
arr5 = [['a', 'b', 'c'], ['a', 'b', 'c', ['a', 'b', 'c']]]

arr2 = dup_arr(arr1)
arr6 = dup_arr(arr5)

p arr1.object_id != arr2.object_id
p arr6.object_id != arr5.object_id

p arr1[0].object_id != arr2[0].object_id
p arr6[0].object_id != arr5[0].object_id

 # Should output 4 trues.