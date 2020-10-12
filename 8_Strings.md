# 1. Strings



1. #### What is a String?

   a. String is a sequence of characters.

   b. ***System.String*** class is used to represent a string

   c. String is ***immutable*** (cannot be updated once created)

   d. Maximum size of a string is ***2GB*** or 1 Billion Characters



2. #### How to Declare a string in C#?

   ```c#
   // Mehtod 1 - using "string" keyword
   string s = "Hello World";
   
   // Method 2 - using "String" class
   String s = "Hello World";
   ```

   

3. #### Difference between "String" & "string"?

   ​	a. ***string*** keyword is just an alias for **"System.String".**

   ​	b. It is same like, ***"int"*** & ***"System.Int32"***

   ​	c. ***string*** should be used while creating string objects, ***String*** is used to access string methods.

   ​	d. string keyword is compiled to "System.String" after compilation to MSIL.



4. #### How to read string from console?

   ```c#
   string s = Console.ReadLine();
   ```





# 2. String Properties & Methods



1. ***Length***

   ```c#
   string s = "Hello World";
   
   s.Length;	// 11
   ```



2. **Contains()**

   Check if a given string is a substring

   ```c#
   string s = "Hello World";
   
   s.Contains("World");	// true
   s.Contains("Prajwal");	// false
   ```

   





