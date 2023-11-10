# Program-to-find-Smallest-element-in-an-array-using-C

Smallest Element in an array in C
Here, in this page we will discuss the program to find the smallest element in an array in C programming language. We apply algorithm that assumes the first element as smallest element and then compare it with other elements if an element is smaller than it then, it becomes the new smallest element, and this process is repeated till complete array is scanned.

Smallest element in an array in C
While loop in C
Methods Covered
Method 1: Simple iterative
Method 2: Top Down recursive
Method 3: Bottom Up Recursive
 
Method 1:-
For a user-defined input num:-

Assign min = arr[0]
Linearly traverse through the whole array
Whenever you encounter a smaller element (arr[i] < min)
Update min, min = arr[i]
C Program:-
Run
#include <stdio.h>

int getSmallest(int arr[], int len)
{
    // assign first array element as smallest
    int min = arr[0];
    
    // linearly search for the smallest element
    for(int i=1; i < len; i++)
    {
        // if the current array element is smaller
        if (arr[i] < min)
            min = arr[i];
    }
    
    return min;
    
}
int main()
{
    int arr[] = {5, 8, 7, 2, 12, 4};
    
    // get the length of the array
    int len = sizeof(arr)/sizeof(arr[0]);    
    
    printf("The smallest : %d", getSmallest(arr, len));
}
Output
The smallest : 2
Related Pages
Given a string s, remove all its adjacent duplicate characters recursively
 
Find Largest element in an array
 
Find the Smallest and largest element in an array

Find Second Smallest Element in an Array

Calculate the sum of elements in an array 

Method 2 (Using Recursion)
This method requires you to know recursion in C.

Call a function : getSmallest(int arr[], int i, int len, int max)

With initial call up values as : getSmallest(arr, 0, len, arr[0])
Initially passing min as arr[0]
Initially passing ‘i’ as 0
In each recursive call check if current array element is smaller than min
If it is then assign min = arr[i]
Move to the next recursive call trying to do the same thing for the next array index
Stop when you’ve read all elements and reach the bounds of array and print max value
Method 2 C Program:-
Run
// C Program to find smallest element in an array
// using top down recursive approach
#include <stdio.h>

void getSmallest(int arr[], int i, int len, int min)
{
    // base case, when last element was read in previous recursion 
    if(i >= len){
        printf("Smallest: %d", min);
        return;
    }
    
    if(arr[i] < min)
        min = arr[i];
    
    getSmallest(arr, i+1, len, min);
}
int main()
{
    int arr[] = {30, 5, 20, 60, 10, 50, 25};
    
    // get the length of the array
    int len = sizeof(arr)/sizeof(arr[0]);    
    
    getSmallest(arr, 0, len, arr[0]);
    
    return 0;
}
// Time complexity: O(N)
// Space complexity: O(1)
// Auxilary space complexity : O(N) due to function call stack
Output
Smallest: 5
While loop in C
Method 3 (Using Recursion)
This method requires you to know recursion in C. 

Call a function : minimum(int arr[], int i, int end)

With initial call up values as minimum(arr, 0, end)
Initially passing end as the index of last array element
Initially passing ‘i’ as 0
Recursively reach iteration where reading 2nd last element
Find smaller between 2nd last and last array elements
And return the result to min value of the previous recursive iteration
In each of the remaining recursive callups find the smaller b/w current array index element and current min value
Pass final min value from last recursive callup to main and print
Method 3 C Program:-
Run
// C Program to find smallest element in an array
// using bottom up recursive approach
#include <stdio.h>

int minimum(int arr[], int i, int end)
{
    int min;
    
    // when we reach 2nd last array element
    // return the smaller b/w last & 2nd last elements
    if(i == end-1)
        return (arr[i] < arr[i + 1]) ? arr[i] : arr[i + 1];

    min = minimum(arr, i + 1, end);

    return (arr[i] < min) ? arr[i] : min;
}

int main()
{
    int arr[] = {25, 10, 40, 30, 20, 80};
    
    // storing the index of end array element 
    // end = 5 : arr[5] = 80 (the end element)
    int end = sizeof(arr)/sizeof(arr[0]) - 1;    

    int min = minimum(arr, 0, end);

    printf("Smallest: %d\n", min);

    return 0;
}
Output
Smallest: 10
