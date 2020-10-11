# 1. Anonymous Method



1. #### What is an Anonymous Method?

   It is method without any name.



2. #### What is the use of Anonymous Method?

   ​	a. Used to pass function as a parameter.

   ​	b. Used to simply delegate creation process, we don't need to create a method separately before passing to a delegate.

   ```c#
   using System;
   					
   public class Program
   {
   	public delegate void MyDelegate(string s);
   	
   	public static void Main()
   	{
           int a = 4;
           
           // Create Anonymous method using delegate keyword & assign to delegate
   		MyDelegate md = delegate(string s){
   			Console.Write(s);
               
               // Outer variables can be accessed
               Console.Write(a);		// 4
   		};
   		
   		md("Hello Prajwal!");
   	}
   }
   ```

   

   

   c. We can pass anonymous methods as parameter

   ```c#
   using System;
   					
   public class Program
   {
       // Declare Delegate
   	public delegate void MyDelegate(string s);
   	
       // Method to which our anonymous function is passed
   	public static void Fun(MyDelegate md, string color){
   		color += " White";
   		md(color);
   	}
   	
   	public static void Main()
   	{
           // Creating Anonymous method
   		MyDelegate md = delegate(string s){
   			Console.Write(s);
   		};
   		
           // Passing anonymous method as a delegate object
   		Fun(md, "Black");
   		
   	}
   }
   ```

   