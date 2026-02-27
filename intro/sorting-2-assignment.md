# Sorting Algorithms

##  1. Proof that, under the average-case scenario, the insertion sort has a time complexity of O(N<sup>2</sup>) Draw a clear figure and show all the operations clearly. 
  In the average case scenario, we can assume a random input where for each positon j, there are j elements before it and on average half of those elements are greater than A[j]. This means that the averge shifts at each iteration is half of j. A shift needes a
  a comparison and a move which means that for each time we iterate through the  well need j amount of operations. Since we are looping through each j at j until a j > 0 and A[j-1] > a[j]. We can infer a quadradic time complexity.

```
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
}
```
    
  
