Row with maximum number of 1’s in C
Here, in this page we will discuss the program to find the row with maximum number of 1’s in C Programming Language. We are given with an two dimensional array, containing only 0 and 1, each row of the matrix are sorted. We need to print the index of that row, which contain maximum number of 1’s.

Accenture Eligibility Criteria 2023
While loop in C
Method 1 :
Take a variable to hold the index value of required row, let it be index=-1, and max_count=0, that hold the maximum count of 1.
Now, iterate over each row, and take variable say count=0, to count the number of 1’s in current row.
For, i-th row, iterate over the columns and increase the value of count if element is equal to 1.
Check if count > max_count, then set max_count = count and index=i.
After the iteration of each row, print the value of index.
Time and Space Complexity :
Time-Complexity : O(r*c)
Space-Complexity : O(1)
Method 1 : Code in C
Run
#include <stdio.h>

int main(){

   int mat[4][4] = {{0, 0, 0, 1}, 
                    {0, 1, 1, 1}, 
                    {1, 1, 1, 1}, 
                    {0, 0, 0, 0}};

   int max_count=0, index=-1;

   for(int i=0; i<4; i++){
     int count = 0;
     for(int j=0; j<4; j++){ 
         if(mat[i][j]==1) 
            count++; 
         
     } 
     if(count>max_count)
     {
        max_count = count;
        index = i;
     }
   }

   printf("Index of row with maximum 1s is %d", index);

}
Output :
Index of row with maximum 1's is 2						
Method 2 (Using Binary Search) :
Take a variable to hold the index value of required row, let it be index=-1, and max_count=0, that hold the maximum count of 1.
Now, iterate over each row, and take variable say count=0, to count the number of 1’s in current row.
For, i-th row, use binary search to find the first instance of 1.
Then count = No. of columns – first instance of 1.
Check if count > max_count, then set max_count = count and index=i.
After the iteration of all rows, print the value of index.
Time and Space Complexity :
Time-Complexity : O(r*log(c))
Space-Complexity : O(1)
Method 2 : Code in C
Run
#include <stdio.h>

int first(int arr[], int low, int high)
{
    if(high >= low)
    {
      int mid = low + (high - low)/2;
      if ( ( mid == 0 || arr[mid-1] == 0) && arr[mid] == 1)
        return mid;

      else if (arr[mid] == 0)
        return first(arr, (mid + 1), high);

      else
        return first(arr, low, (mid -1));
     }
     return -1;
}


int main(){

   int mat[4][4] = {{0, 0, 0, 1}, 
                    {0, 1, 1, 1}, 
                    {1, 1, 1, 1}, 
                    {0, 0, 0, 0}};

   int max_count=0, index=-1;

   for(int i=0; i<4; i++){ int count = 0; int x = first(mat[i], 0, 3); if(x!=-1) count = 4-x; if(count>max_count){
                max_count = count;
                index = i;
     }
   }

   printf("Index of row with maximum 1s is %d", index);

}
Output :

Index of row with maximum 1's is 2
