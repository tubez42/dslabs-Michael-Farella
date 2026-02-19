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
### 4. Use Big O Notation to describe the time complexity of the following function, which accepts an array of strings and prints each string in multiple cases:
```
def multiple_cases(array) 
	array.each do |string|
		puts string.upcase 
		puts string.downcase 
		puts string.capitalize
	end 
end
```
We see the same amount of total compelxity in this function as the previous. The only difference is that we are modifing through the array 3N instead of 2N. The big O notation time complexity remains the same however at O(n).

### 5. The next function iterates over an array of numbers, and for each number whose index is even, it prints the sum of that number plus every number in the array. What is this function’s efficiency in terms of Big O Notation?
```
def every_other(array) 
	array.each_with_index do |number, index|
		if index.even?
			array.each do |other_number|
            	puts number + other_number
			end 
		end
	end 
end
```
Let's break down the sources of time complexity. First we have both an inner and outer loop in our function. The outerloop iterates through all elements 
 in the function with time compelxity O(n) and enters the second loop in half the cases (since its even). The innerloop is more complex as it requires and entire additonal loop through the array in order to create the sum of all other numbers. Putting the inner and outer loop complexities together we get O(n)<sub>/2</sub> + O(n<sup>2</sup>) = O(n<sup>2</sup>).


