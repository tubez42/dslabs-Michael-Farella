# Activity 2 Searching 
## 1. How many steps would it take to perform a linear search for the number 8 in the ordered array, [2, 4, 6, 8, 10, 12, 13]? 
  In a linear search, the elements are checked one by one to match the key element. In this array the number 8 lies at index 3,
  therefore it will take 4 steps to search for 8 or O(4).
## 2. How many steps would binary search take for the previous example? 
  A binary search, takes the a range and tests the middle index as its selection. If there is no clear divison we may use the floor of its divison as next index to test. In the given array it would first test index
  is index 2, which it would read a 6, then it would select index 4 which it would find 10, and then finally it would guess index 3 taking O(3). This aligns with O(log<sub>2</sub> n) runtime for
  binary search algorithm.
## What is the maximum number of steps it would take to perform a binary search on an array of size 100,000? 
  From the runtime equation we can assume it will take 17 steps to perform a binary search
  on an array of 100,000 items. log<sub>2</sub> 100000 ≈ 17.
## Write a C++ program that implements both linear search and binary search algorithms using an array of 100,000 elements. The program should record and report the number of steps (comparisons) performed during each search operation. In addition, analyze and justify the observed behavior by providing a theoretical explanation using Big-O notation, demonstrating why linear search exhibits O(N) complexity and binary search exhibits O (logN) complexity.
``` C++
#include <iostream>
#include <vector>
#include <random>
using namespace std;

const int SIZE = 100000;

//Linear Search
int linearSearch(int arr[], int size, int key, int &steps) {
        /*pass array, size value, key, and reference to update amount of steps, same for binary search */
    for (int i = 0; i < size; i++) {
        steps++;                 // count number of steps taken
        if (arr[i] == key)
            return i;
    }
    return -1;
}

/* Binary Search */
int binarySearch(int arr[], int size, int key, int &steps) {
    int low = 0;
    int high = size - 1;

    while (low <= high) {
        steps++;                 // step is created by each new mid value tested
        int mid = (low + high) / 2; //using int division automatically takse floor divison

        if (arr[mid] == key)
            return mid;
        else if (arr[mid] < key) // look right
            low = mid + 1;
        else
            high = mid - 1;     //look left
        
    }
    return -1;
}
int main() {
    int arr[SIZE];

    // Fill array with sorted values
    for (int i = 0; i < SIZE; i++)
        arr[i] = i + 1;

    int key = 100000;   // try last element (worst case for linear search)

    int linearSteps = 0; //step counters
    int binarySteps = 0;

    int linearIndex = linearSearch(arr, SIZE, key, linearSteps);
    int binaryIndex = binarySearch(arr, SIZE, key, binarySteps);

    //output
    cout << "Linear Search Index: " << linearIndex << endl;
    cout << "Linear Search Steps: " << linearSteps << endl << endl;

    cout << "Binary Search Index: " << binaryIndex << endl;
    cout << "Binary Search Steps: " << binarySteps << endl;

    return 0;
}

```
<img width="285" height="162" alt="Act2prob4output" src="https://github.com/user-attachments/assets/b9d069ef-b645-43b4-bf36-d60341457d0b" />

As you can see when we test N values using each search method they take the respective theoretical amount of steps. Where Linear Search has O(N) complexity and the Binary Search has O(logN) search time.

###  5. Write pseudocode for a randomized search algorithm that searches for a given key by randomly selecting indices without repetition. Use a dataset of 100,000 distinct elements, stored in a vector. Each element may be examined at most once during the search. Analyze and state the best-case, average-case, and worst-case time complexities of this algorithm using Big-O notation.
```
C++
/*
*randomizedSearch(vector V, key):

n = size of V
visited = boolean array size n initalized to false
steps = 0

while (not all values in visited are true):
i = randomly choose an index from 0 to n-1

if visited[i] = true:
continue

visited[i] = true
steps = steps + 1

if V[i] == key:
return (i, steps)

return (-1, steps)   // key not found
*/
```
  


### Then, implement the algorithm in C++, using only the following standard headers: <vector> for data storage, <random> for random index generation, and <iostream> for input and output. The implementation should track and report the number of comparisons performed during the search.
```
C++
#include <iostream>
#include <vector>
#include <random>
using namespace std;

int randomizedSearch(const vector<int>& data, int key, int& steps) {
    /*arguments: vector of data points, key, reference to steps value */

    /*boolean array to ensure we have non-recurrent visits, size of our data array, init with false values*/
    int n = data.size();
    vector<bool> visited(n, false);

    /*random value generation*/
    random_device rd;
    mt19937 gen(rd());
    uniform_int_distribution<> dist(0, n - 1);

    int visitedCount = 0;
    /*while loop checks to make sure the amount of visited values is less than n */
    while (visitedCount < n) {
        /*generate value */
        int index = dist(gen);
        /*test if value has been tested previously if so generate new value*/
        if (visited[index])
            continue;
        /* update boolean array, update count for while loop, and steps for step counter*/
        visited[index] = true;
        visitedCount++;
        steps++;
        /*check for key value and return if successful*/
        if (data[index] == key)
            return index;
    }
    /*return error if no value is found*/
    return -1;
}

int main() {

    /*initalize data vector*/
    const int SIZE_5 = 100000;
    vector<int> data(SIZE_5);

    // Fill vector with distinct values
    for (int i = 0; i < SIZE_5; i++)
        data[i] = i + 1;

    int key_5 = 100000;   // try case N
    //init and run function
    int steps = 0;
    int index = randomizedSearch(data, key_5, steps);
    //output
    cout << "Found at index: " << index << endl;
    cout << "Comparisons performed: " << steps << endl;




    return 0;
}
```
<img width="287" height="98" alt="Screenshot 2026-02-15 120421" src="https://github.com/user-attachments/assets/acc012b9-a84c-4802-91fc-5ee4254438fc" />


### Finally, compare and contrast the randomized search algorithm with linear search and binary search in terms of time complexity, data requirements (such as ordering), and practical efficiency. Discuss scenarios in which each approach may be preferred, highlighting the advantages and limitations of randomized search relative to linear and binary search.

Since randomized search still can have the worst case scenario where it generates a value at the last possible index it has O(N) time complexity.  However, we can see from its use it may return values quicker than a linear search. Additionally, unlike a binary search it does not require the array to be ordered. Which may make it a similarly viable option to linear searches when looking at unordered data sets.


