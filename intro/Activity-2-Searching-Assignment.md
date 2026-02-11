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
## Write a C++ code that implements the linear and binary search algorithms. The algorithm should be able to calculate the number of steps against the given search.
``` C++
#include <iostream>
#include <vector>
using namespace std;

int linearSearch( const vector<int>& v, vector<int>& d, int key) {
    /*3 arguments, v is our array, d is an array to store matching
     *index value(using an array if we wish store multiple matching indices), and a key argument
     */
    int steps = 0; // step counter init
    for(int i = 0; i < v.size();i++) {
            /*for loop to iterate through array
            well consider each iteration through the loop as a step
            as it is an evaluation of a given index
            and increment our counter
                */
        steps++;
        if(v[i] == key) /* testing index against key*/
        {
            /*key is found index is pushed onto result array and we exit the loop via return*/
            d.push_back(i);
            return steps;
        }
    }
    steps = -1;
    return steps;
}

int BinarySearch( const vector<int>& v, vector<int>& d, int key)
{
    /*reuse arguments from linearSearch*/
    /*
     *extra local variables
     *low, high, and mid to determine and test middle values
     *implement int divison to use floor division
     **/
    int low = 0;
    int high = v.size() - 1;
    int mid = (low + high) / 2;
    int steps = 0;
    while(low <= high)
    {
        /*
         *loop continues through case where the range is  greater than 0
         *otherwise no such case exists and we return with -1 steps to determine it was not found
         *in every step we determine a new mid value to test and therefore the step counter should
         * increase everytime a new mid is determined and tested.
         */
        steps++;
        mid = (low + high) / 2;
        if(v[mid] == key)
        {
            d.push_back(mid); // key is found and exit loop
            return steps;


        }
        else if(v[mid] > key)
        {
            high = mid - 1; // searching the left
        }
        else
        {
            low = mid + 1; // searching the right half
        }


    }
    steps = -1; // key is not found
    return steps;

}

int main() {
    vector<int> data = {3, 8, 15, 23, 15};
    vector<int> data_index;
     cout << "Steps for linear search: " << linearSearch(data, data_index, 3) << endl;
    for (int x: data_index) {
        cout << "Index: " << x << endl;
    }

    data_index.clear();

    cout << "Steps in Binary Search: " << BinarySearch(data, data_index, 3) << endl;
    for (int x: data_index)
    {
        cout << "Index: " << x << endl;
    }

    return 0;
}
```
