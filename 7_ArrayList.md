# 1. ArrayList



1. #### What is ArrayList in C#?

   ​	a. It is a ***non-generic*** collection.

   ​	b. Defined in ***System.Collections*** namespace

   ​	c. It is ***dynamic*** sized array

   ​	d. It contains data of ***same*** or ***different*** data types

   ​	e. It implements following Interfaces:

   ​			a. IEnumerable

   ​			b. ICollection

   ​			c. IList

   ​			d. IClonable

   ```c#
   ArrayList dynamicArray = new ArrayList();
   
   dynamicArray.Add(1);
   dynamicArray.Add(4.5);
   dynamicArray.Add("Hello");
   dynamicArray.Add('V');
   
   foreach(var item in dynamicArray){
       Console.Write(item);
   }
   ```



​	

f. Get ***Count*** & ***Capacity*** of ArrayList

```c#
ArrayList list = new ArrayList();

list.Add(1);
list.Add("Hello World");
list.Add('V');

// Get count of elements
list.Count;		//	3

// Get Capacity
list.Capacity;	// 8
```





g. ***Remove*** elements from ArrayList

```c#
ArrayList list = new ArrayList();

list.Add(1);
list.Add("Hello");
list.Add('r');

// 1st Option
list.Remove(1);

// 2nd Option
list.RemoveAt(1);

// To remove all elements from list
list.Clear();
```





h. ***Sort*** elements in ArrayList

```c#
ArrayList list = new ArrayList();

list.Add(5);
list.Add(4);
list.Add(3);

list.Sort();
```





# 2. Difference between Array & ArrayList



| Array                                   | ArrayList                                     |
| --------------------------------------- | --------------------------------------------- |
| **Fixed** Size                          | **Dynamic** Size                              |
| Can sore elements of **same** data type | Can store elements of **different** data type |
| System.Array Class is used              | **System.Collections** class is used          |
| **Null** value cannot be inserted       | **Null** can be inserted                      |





# 3. Convert ArrayList to Array



1. ***ToArray*** Method

   ```c#
   ArrayList list = new Array();
   
   list.Add(1);
   list.Add(2);
   list.Add("Hello");
   
   // If elements are of different type
   object[] array = list.ToArray();
   
   // If elements are of same type
   int[] array = (int[])list.ToArray(typeof(string)); // This will give exception for diferent data type
   ```

   