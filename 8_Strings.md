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

   
   
3. **ToUpper**()

   Convert all characters in string to uppercase

   ```c#
   string s = "hello";
   
   s = s.ToUpper();	// HELLO
   ```

   

4. **ToLower**()

   convert all characters of string to lowercase

   ```c#
   string s = "HELLO";
   s = s.ToLower();	// hello
   ```



5. **Trim**()

   Remove spaces from start & end

   ```c#
   string s = "     hello     ";
   s = s.Trim();	//	hello
   ```

   

6. **ToCharArray**()

   Generate an array of characters from a string

   ```c#
   string s = "hello";
   
   char[] charArray = s.ToCharArray();	// ['h','e','l','l','o']
   ```

   

7. **Substring**()

   Get a substring from a string

   ```c#
   string s = "Hello World";
   
   // Start from 0th element and print 4 elements
   s = s.Substring(s,0,4); 	// Hell
   ```

   

8. **StartsWith**()

   ```c#
   string s = "Hello";
   s.StartsWith("He");	// true
   s.StartsWith("ll");	// false
   ```



9. **Split**()

   Split the string into a string array based on a character

   ```c#
   string s = "Hello";
   string s2 = "Hello-Prajwal-Sharma";
   
   string[] c = s.Split('');	// ["H","e","l","l","o"]
   
   string[] c2 = s2.Split('-');	// ["Hello","Prajwal","Sharma"]
   ```



10. **Replace**()

    Replace substring in a string

    ```c#
    string s = "Hello World";
    
    s = s.Replace("World", "Prajwal");	// Hello Prajwal
    ```



11. **Convert array of character to a string**

    ```c#
    char[] c = {'H','e','l','l','o',' ','W','o','r','l','d'};
    
    string s = new String(c);	// Hello World
    ```

    

12. **How to declare empty string**

    ```
    string s = String.Empty;
    string s = "";
    string s = null;
    ```

    



# 3. StringBuilder



1. It is a dynamic object which is mutable.
2. It dynamically increases the current allocated memory to accommodate new string.
3. Default capacity of a StringBuilder object is ***16***.

<img src="https://media.geeksforgeeks.org/wp-content/uploads/20190310161026/Presentation12.jpg" alt="img" style="zoom:50%;" />

3. #### How to declare StringBuilder?

   ```c#
   using System.Text;
   
   // Method 1
   StringBuilder sb = new StringBuilder();
   
   // Method 2
   StringBuilder sb = new StringBuilder("Hello World");
   ```

   

4. #### StringBuilder Methods

   ```c#
   StringBuilder sb = new StringBuilder();
   
   // Length Property
   sb.Length;
   
   // Append
   sb.Append("Hello");
   sb.Append("World");		// HelloWorld
   
   // AppendLine
   sb.AppendLine("Hello");
   sb.Append("World");			// Hello \n World
   
   // AppendFormat
   sb.AppendLine("Hello");
   ab.AppendFormat("{0:C}",50);	// Hello \n Rs50
   
   // Insert
   StringBuilder sb = new StringBuilder("Hello", 20);
   sb.Insert(6, "World");	// Hello World
   
   // Remove
   sb.Remove(0,3);	// lo
   
   // Replace
   sb.Replace("World", "Prajwal");	// Hello Prajwal
   
   // Clear
   sb.Clear();	// Remove all characters from string
   ```





# 4. Difference between String & StringBuilder

​	

1. #### When should we use string or StringBuilder?

   Use string when a string is not going to update, Use StringBuilder if you are frequently changing the string.

| String                    | Stringbuilder |
| ------------------------- | ------------- |
| Immutable                 | Mutable       |
| Costly to update a string | Not Costly    |

