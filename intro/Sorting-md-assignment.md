### 1. Use Big O Notation to describe the time complexity of an algorithm that takes 4N + 16steps.
  Since Big O Notation does not concern itself with constant values or priortizes the highest degree polynomial, the time complexity of an algorithm described by 4N + 16 is Linear. This is the same as O(n).
### 2. Use Big O Notation to describe the time complexity of an algorithm that takes 2N<sup>2</sup>.
 In the example of 2N<sup>2</sup> the highest order polynomial is 2. In this case the algorithm would take quadratic time to compute.
 ### 3. Use Big O Notation to describe the time complexity of the following function, which returns the sum of all numbers of an array after the numbers have been doubled:
 ```
def double_then_sum(array) 
	doubled_array = []

	array.each do |number| 
		doubled_array << number *= 2
	end

	sum = 0

	doubled_array.each do |number| 
		sum += number
	end
	return sum 
end
```
Breaking down the function we have two sections which contribue to complexity. The first has us go through the array and double each value within it.
```
array.each do |number| 
		doubled_array << number *= 2
	end
```
This has a time compelxity of O(n) since were doing one operation to each member of N. The second section has us add a value of zero to each number in the array.
```
doubled_array.each do |number| 
		sum += number
	end
```
This task also presents a complexity of O(n). Meaning that the total compleixty is O(n) + O(n)  = 2O(n). Which big O notation interpets as O(n).
###


