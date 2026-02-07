# 1. Explain how to create an array of 100 elements
  Array declaration is fairly straightforward. Simply specify the type of value you'd like to make array of, create a name and assign
a value to the number of elements inside braces.
```C++
int myArray[100];
```
This code for example creates an array of 100 elements.
To populate this array there are a number of different methods such as counter-based, range-based, range-based(reference),
and range-based(constant reference). Here is an example of counter-based population.
```C++
for(int i = 0: i < size(myArray): i++)
  {
    myArray[i] = i;
  }
```
This will populate the array where the cell will hold the value of its respective index.
### 2. What will be the size of each element of an array? (requires C++ code)
The size of each element will vary depending on the data type. 
### char  : 1 byte
### short : 2 bytes
### int   : 4 bytes
### long  : 4 bytes
### float : 4 bytes
### double: 8 bytes
This also can be checked using the sizeof  operator.
```C++
int myElementSize = sizeof(myArray[0]);
cout << myElementSize << " byte(s)" << endl;
//Array elements are all the same size
```
# 3. For an array containing 100 elements, provide the number of steps the following operations would take:
### Reading
  Reading would only take one step, just accessing the specified index.
### Searching
  Searching through an unsorted array requires a linear search, and may take the length of the array (N) amount of steps, in 
    this case 100.
### Insertion at the beginning of the array
  This will require shifting each value to a new memory location and as well as adding the new element meaning it would take
  N+1 or 101 steps.
### Insertion at the end of the array.
  This is much simpler and only requires one step in adding the value to the memory location following the end of the array.
### Deletion at the beginning of the array.
  This requires removing the first value and then shifting each value in the array by 1 costing N -1 steps plus the deletion step.
  so 100 steps.
### Deletion at the end of the array.
  This is just removing the value at the last memory location and only requires 1 step.
# 4 Normally the search operation in an array looks for the first instance of a given value. But sometimes we may want to look for every instance of a given value. For example, say we want to count how many times the value “apple” is found inside an array. How many steps would it take to find all the “apples”? Give your answer in terms of N.
  Since we are looking for every instance of an apple in this case. Each possible case for which an apple could exist in the array
  must be checked. Therefore it is necessary to check all values of the array. The length of array can be represented as N. Since were are examining 
  the entire array we must check N cases.
# 5 How to find the memory address of an array in C++.
The &(reference) operator makes this fairly straightforward in C++.
```C++
int myArray[10];
   cout << "The starting address of myArray is " << &myArray[0] << endl;
   cout << "The second address of myArray is " << &myArray[1] << endl;
   cout << "The last address of myArray is " << &myArray[size(myArray)] << endl;
```

<img width="392" height="67" alt="step 6 proof" src="https://github.com/user-attachments/assets/9e335c2e-6822-4543-b5ef-b8e4903665c7" />
