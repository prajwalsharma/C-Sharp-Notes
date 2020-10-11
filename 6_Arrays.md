# 1. Arrays



1. #### Array Declaration (One Dimensional)

   ```c#
   // Array Declaration with size - all elements will be zero
   int[] array = new int[5];
   string[] array = new string[5];	
   
   // Array declaration with initialization
   int[] array = new int[5] {1,2,3,4,5};
   string array = new string[3]{"Hi","Hello","Prajwal"}
   
   // Array initialization without size
   int[] array = {1,2,3,4,5};
   ```

   

2. #### Multidimensional Array

   Arrays having rows & columns

   ```c#
   // 2D Array Declaration with 4 rows & 2 columns
   int[,] array = new int[4,2];
   
   // 2D array declaration with initialization
   int[,] array = new int[,]{
       {1,2},
       {2,3},
       {3,4},
       {4,5}
   }
   
   int[,] array = new int[4,2]{
       {1,2},
       {2,3},
       {3,4},
       {4,5}
   };
   
   // Access elements from 2D array
   array[0,0];	// 1
   array[0,1];	// 2
   array[1,0];	// 2
   ```

   

3. #### Jagged Arrays

   ​	a. Array of arrays

   ​	b. Only need to specify number of rows while declaring, if columns are mentioned then this will not remain jagged array.

   ```c#
   // Declaration - having 2 arrays
   int[][] array = new int[2][];
   
   int[] a = {1,2,3};
   int[] b = {4,5,6};
   
   array[0] = a;
   array[1] = b;
   
   // Declaration with initialization
   int[][] array = {
       new int[] {1,2,3},
       new int[] {4,5,6}
   };
   
   // Accessing Elements
   array[0][0];	// 1
   array[1,1];		// 5
   ```





# 2. Array Properties



1. **Length**

   Gives number of elements present in array (length/size)

   ```c#
   int[] array = new int[] {1,2,3,4,5,6,7,8};
   
   array.Length;	// 8
   
   string[] array = {"Hello", "Prajwal"};
   
   array.Length;	// 2
   ```

   

2. **Rank**

   Gives the dimension of the array

   ```c#
   int[] array = {1,2,3,4,5};
   
   array.Rank;		// 1 - 1D array
   
   int[,] array = {
       {1,2,3},
       {4,5,6}
   };
   
   array.Rank;		// 2 - 2D array
   ```

   



# 3. Array Methods



1. **BinarySearch**

   Method to search an element in a sorted array using Binary Search Algorithm (log n)

   ```c#
   int[] array = {5,4,3,2,1};
   
   // Boxing
   object item = 3;	// Value to search
   
   // Array must be sorted for BinarySearch
   Array.Sort(array);
   
   int index = Array.BinarySearch(array, item);	// -ve value means not found, else index is returned
   ```

   

2. **Clear**

   Clearing specified range of elements in an array to default value

   ```c#
   int[] a = {1,2,3,4,5};
   
   Array.Clear(a, 1, 2);		// [1,0,0,3,4,5]
   
   // Parameters
   //array: Array
   //index: from where should we start clearing
   //length: how many elements should be cleared
   
   ```

   

3. **ForEach**

   Performs a specified action on all array elements using array

   ```c#
   int[] array = {1,2,3,4,5};
   
   // Declaring Action Delegate
   Action<int> action = SetSquare;
   
   // Declaring method
   pubic void SetSquare(int a){
       Console.Write(a*a);
   }
   
   Array.ForEach(array, action);	// [1,4,9,16,25]
   ```

   

4. **IndexOf**

   Gets first index of a specific element from the array

   ```c#
   int[] array = {1,2,3,4,5};
   
   array.IndexOf(4);	// 3
   array.IndexOf(7);	// -1
   ```

   

5. **LastIndexOf**

   Get last index of a specific element from the array

   ```c#
   int[] array = {1,2,3,4,4,5};
   
   array.LastIndexOf(4);	// 4
   ```

   

6. **Reverse**

   Reverse the array

   ```c#
   int[] array = {1,2,3,4,5};
   
   Array.Reverse(array);
   ```



7. **Sort**

   Sort the array in ascending order

   ```c#
   int[] array = {5,4,3,2,1};
   
   Array.Sort(array);	// [1,2,3,4,5]
   ```

   

8. **Equals**

   Check if two arrays are equal or not

   ```c#
   int[] a = {1,2,3,4,5};
   int[] b = {1,2,3,4,5};
   int[] c = {1,2,3};
   
   a.Equals(b);	// true
   b.Equals(c);	// false
   ```

   

9. Sort array in Descending order

   ```c#
   int[] a = {5,4,3,2,1};
   
   // Method 1
   Array.Sort(a);
   Array.Reverse(a);
   
   // Method 2
   a = a.OrderByDescending(c => c).ToArray();
   ```

   





























