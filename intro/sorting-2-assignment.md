# Sorting Algorithms

##  1. Proof that, under the average-case scenario, the insertion sort has a time complexity of O(N<sup>2</sup>) Draw a clear figure and show all the operations clearly. 
  In the average case scenario, we can assume a random input where for each positon j, there are j elements before it and on average half of those elements are greater than A[j]. This means that the averge shifts at each iteration is half of j. A shift needes a
  a comparison and a move which means that for each time we iterate through the  well need j amount of operations. Since we are looping through each j at j until a j > 0 and A[j-1] > a[j]. We can infer a quadradic time complexity.

  In order prove that it works, I created some code that generates sample arrays and an implementation of insertion sort that counts comparisons and shifts.

``` C++
#include <iostream>
#include <vector>
#include <random>
using namespace std;

//Generate sample vectors
vector<int> generateRandomArray(int size) {
    vector<int> arr(size);

    random_device rd;                // seed
    mt19937 gen(rd());
    uniform_int_distribution<> dist(1, 100);  // range 1–100

    for (int i = 0; i < size; i++) {
        arr[i] = dist(gen);
    }

    return arr;
}
//Function to print array
void printArray(const vector<int>& arr) {
    for (int num : arr) {
        cout << num << " ";
    }
    cout << endl;
}
void insertionSort(vector<int>& arr, long long& comparisons, long long& shifts) {
    int n = arr.size();

    comparisons = 0;
    shifts = 0;

    for (int j = 1; j < n; j++) {
        int key = arr[j];
        int i = j - 1;

        while (i >= 0) {
            comparisons++;  // count comparison

            if (arr[i] > key) {
                arr[i + 1] = arr[i];
                shifts++;   // count shift
                i--;
            } else {
                break;
            }
        }

        arr[i + 1] = key;  // final placement not a shift
    }
}

int main() {
    long long comparisons, shifts;
    vector<int> arr10  = generateRandomArray(10);
    vector<int> arr15  = generateRandomArray(15);
    vector<int> arr20  = generateRandomArray(20);
    vector<int> arr50  = generateRandomArray(50);
    //N = 10
    cout << "Array of size 10:\n";
    printArray(arr10);
    insertionSort(arr10, comparisons, shifts);
    cout << "Sorted array: ";
    for (int num : arr10) {
        cout << num << " ";
    }

    cout << "\nComparisons: " << comparisons;
    cout << "\nShifts: " << shifts;
    comparisons = 0;
    shifts = 0;

    //N = 15
    cout << "\nArray of size 15:\n";
    printArray(arr15);
    insertionSort(arr15, comparisons, shifts);
    cout << "Sorted array: ";
    for (int num : arr15) {
        cout << num << " ";
    }

    cout << "\nComparisons: " << comparisons;
    cout << "\nShifts: " << shifts;
    comparisons = 0;
    shifts = 0;
    //N = 20
    cout << "\nArray of size 20:\n";
    printArray(arr20);
    insertionSort(arr20, comparisons, shifts);
    cout << "Sorted array: ";
    for (int num : arr20) {
        cout << num << " ";
    }

    cout << "\nComparisons: " << comparisons;
    cout << "\nShifts: " << shifts;
    comparisons = 0;
    shifts = 0;

    //N = 50
    cout << "\nArray of size 50:\n";
    printArray(arr50);
    insertionSort(arr50, comparisons, shifts);
    cout << "Sorted array: ";
    for (int num : arr50) {
        cout << num << " ";
    }

    cout << "\nComparisons: " << comparisons;
    cout << "\nShifts: " << shifts;
    comparisons = 0;
    shifts = 0;

    return 0;
}}

```
   ### Here is an example output: 
  <img width="994" height="528" alt="sorting4p1" src="https://github.com/user-attachments/assets/9e5f545f-ff9d-4621-b307-395be026b9e0" />
  
  ### Here is an that output in a line graph with the comparisons and shifts summed.
  <img width="765" height="476" alt="sizeofarray" src="https://github.com/user-attachments/assets/c8d6e679-12d8-4ab5-b76a-451c1fdd9ed6" />

As you can see there is exponetial growth as the array grows in complexity.

# 2. At the start of the insertion sort, the index of the inspected value is set to 1. Change the index of the inspected value and verify that the total number of operations equals 20. Consider the worst-case scenario. Use N=5, where N is the number of elements.
  In the worst case scenario the data will be sorted in reverse order.<br>
  
  [5,4,3,2,1] <br>
  
  j = 1, we have one comparison with index 0 and have one shift = 2 <br>

  j = 2, we compare with indices 1 and 0 which is 2 comparisons and 2 shifts = 4.<br>

  j = 3, Compare with indices 2 ,1, 0 which is 3 comparisons and 3 shifts = 6. <br>

  j = 4, Compare with indices 3, 2, 1, 0 = 8 <br>
  
  2 + 4 + 6 + 8 = 20.<br>

# 3. The following function returns whether or not a capital “X” is present within a string.
```
function containsX(string) {
	foundX = false;
	for(let i = 0; i < string.length; i++) { 
		if (string[i] === "X") {
			foundX = true; 
		}
	}
	return foundX; 
}
```
# (a) What is this function’s time complexity regarding Big O Notation?
# (b) Then, modify the code to improve the algorithm’s efficiency for best- and average-case scenarios.

(a) This algorithm scans through the argued string and changes a boolean value if it finds a value of X within it. It's complexity is linear to the length of the string (N). Therefore it has O(N) time complexity.
(b) Once they  X value is found the code still continues through the string. If an X were to exist at index zero the code would still take N steps to complete. If we gave the code the ability to exit after the X was found, our time complexity would be reduced to from N to, the index of the X J, to O(N - J).
```
function containsX(string) {
	foundX = false;
	for(let i = 0; i < string.length; i++) { 
		if (string[i] === "X") {
			foundX = true;
      return foundX;
		}
	}
	return foundX; 
}
```

  

