# 1. Delegates



1. #### What are Delegates in C#?

   ​	a. It is an object that contains reference of a method.

   ​	b. It is a user defined data type.

   ​	c. It is not a member of the class



2. #### Why do we use Delegates?

   ​	a. Delegates help us to create loosely coupled code.

   ​	b. We're not calling a function directly, instead we are calling delegate and passing reference of our method.

   ​	c. To pass methods as a parameter at runtime.

   ​	d. Used in situations when we need to call a particular method but we don't know which method to call.

   ​	e. Example, I've a button and there are 3 methods, while creating that button I don't know which function to call, therefore 		I'll create a delegate and then resolve that delegate to a particular method at run time.

   ```c#
   public class Calculate{
       
       public delegate void Add(int a, int b);			// Delegate declaration
       public delegate void Sub(int a, int b);
       
       public void AddNum(int x, int y){
           Console.Write(x+y);						// Method supporting delegate signature
       }
       
       public void SubNum(int x, int y){
           Console.Write(x-y);						// Method supporting delegate signature		
       }
       
       public static void Main(){
           Calculate calc = new Calculate();
           
           Add add = new Add(obj.AddNum);			// Passing reference of method to delegate
           Sub sub = new Sub(pbj.SubNum);			// Passing reference of method to delegate
           
           add(1,3);		// 4	- Calling method through delegate
           sub(5,3);		// 2	- Calling method through delegate
       }
       
   }
   ```

   ```c#
   public class Program
   {
       // Declare a Delegate
   	public delegate void saveFile(string s);
   	
       // Create a method whose reference will be passed to Delegate
   	public void SaveToFile(string s){
   		Console.WriteLine("Saved to file");
   	}
   	
   	public void SaveToDatabase(string s){
   		Console.WriteLine("Saved to DB");
   	}
   	
   	public static void Main()
   	{
   		Program p = new Program();
   		
           // Create instance of a Delegate & pass method as reference
   		saveFile sf1 = new saveFile(p.SaveToFile);
   		saveFile sf2 = new saveFile(p.SaveToDatabase);
           
           // If methods are static
   		saveFile sf1 = new saveFile(SaveToFile);
   		saveFile sf2 = new saveFile(SaveToDatabase);
   		
           // Call the method through Delegate
   		sf1("Hello");
   		sf2("World");
   	}
   }
   ```

   





# 2. Multi-Cast Delegates



1. #### What is Multicasting of a Delegate?

   ​	a. It is an extension of normal delegates, in which we can call multiple methods with a single call from delegate.

   ​	b. Methods are called in FIFO order.

   ​	c. Use "+" or "+=" to add methods

   ​	d. Use "-" or "-=" to remove methods

   ```c#
   using System;
   					
   public class Program
   {
       // Delegate Declaration
   	public delegate void RectangleDelegate(double h, double w);
   	
       // Method declaration, invoked by Delegate
   	public static void Area(double x, double y){
   		Console.WriteLine("Area: " + x*y);
   	}
   	// Method declaration, invoked by Delegate
   	public static void Perimeter(double x, double y){
   		Console.WriteLine("Perimeter: " + 2*(x+y));
   	}
   	
   	public static void Main()
   	{
           // Passing reference of first method
   		RectangleDelegate rd = new RectangleDelegate(Area);
           
           // Adding another method (Multicasting)
   		rd += Perimeter;
           
           // Invoking Delegate
   		rd(3.4, 5.6); or rd.Invoke(3.4, 5.6)			// Area: 19.04
           												// Perimeter: 18
           
           rd(5.6, 7.8); or rd.Invoke(5.6, 7.8)			// Area: 43.68
           												// Perimeter: 26.8
   	}
   }
   ```

   



# 3. Predicate Delegate



1. #### What is a Predicate Delegate?

   ​	a. It is a built-in generic type delegate.

   ​	b. It makes our code short & more readable.

   ​	c. It supports only those methods that return either true or false (**boolean**)

   ​	d. We can pass Only 1 parameter to the function

   ```c#
   using System;
   					
   public class Program
   {
   	
   	public static bool Check(string s){
   		if(s.Length < 7){
   			return true;
   		}
   		else 
   			return false;
   	}
   	
   	public static void Main()
   	{
           // Creating a Predicate Delegate and assigning method reference
   		Predicate<string> p = Check;
           
           // Call the method through Predicate Delegate
   		Console.Write(p("Hellosdsdsd"));				// false
   	} 
   }
   ```

   

   

   d. It can also used with Anonymous Methods

   ```c#
   using System;
   					
   public class Program
   {
   	public static void Main()
   	{
           // Declaring a Predicate Delegate & declaration of Anonymous method and assigning reference
   		Predicate<string> p = delegate(string s){
   			if(s.Length < 7){
   				return true;
   			}
   			else 
   				return false;
   		};
   		Console.Write(p("Hellosdsdsd"));
   	} 
   }
   ```

   

   

   e. It can also be written as Lambda Expression

   ```c#
   using System;
   					
   public class Program
   {
   	public static void Main()
   	{
   		Predicate<string> p = (s) => (s.Length < 7 ? true : false);
   		Console.Write(p("Hellosdsdsd"));	// False
   	} 
   }
   ```





# 4. Action Delegate



1. #### What is an Action Delegate?

   ​	a. It is a built-in generic Delegate.

   ​	b. It makes our code short & readable.

   ​	c. We can pass 1-16 parameters to the function.

   ​	d. This method does not return anything (return type void)

   ```c#
   using System;
   					
   public class Program
   {
       // Only methods having return type void are allowed
   	public static void Fun(int a, int b){
   		Console.Write(a+b);
   	}
   	
   	public static void Main()
   	{
           // Declaring Action Delegate & assigning reference of Method Fun
   		Action<int, int> f = Fun;
           	or
           Action<int, int> f = new Action<int, int>(Fun);
   		
           // Invoking method through Delegate
   		f(1,2);		// 3
   	}
   }
   ```

   ​	

   

   e. It can also used with anonymous methods

   ```c#
   using System;
   					
   public class Program
   {
   	public static void Fun(int a, int b){
   		Console.Write(a+b);
   	}
   	
   	public static void Main()
   	{
   		Action<int, int> f = delegate(int a, int b){
   			Console.Write(a+b);
   		};
   		
   		f(1,2);		// 3
   	}
   }
   ```

   

   

   f. It can also used with Lambda Expression

   ```c#
   using System;
   					
   public class Program
   {
   	public static void Fun(int a, int b){
   		Console.Write(a+b);
   	}
   	
   	public static void Main()
   	{
   		Action<int, int> f = (a,b) => (Console.Write(a+b));
   		
   		f(1,2);		// 3
   	}
   }
   ```

   



# 5. Func Delegate



1. #### What is Func Delegate?

   ​	a. It is a built in Delegate.

   ​	b. It makes our code shorter & readable.

   ​	c. It eliminates the step of declaring custom delegates.

   ​	d. It is used when we need to return a value from our function.

   ​	e. The last parameter is always the "***out***" parameter.

   ```c#
   using System;
   					
   public class Program
   {
   	public static int Add(int a, int b){
   		return a+b;
   	}
   	
   	public static void Main()
   	{
   		Func<int, int, int> f = Add;		// 3rd Parameter is out Parameter
   		int a = f(1,2);
   		Console.Write(a);		// 3
   	}
   }
   ```

   

   

   f. Can be used with Anonymous methods

   ```c#
   using System;
   					
   public class Program
   {
   	public static int Add(int a, int b){
   		return a+b;
   	}
   	
   	public static void Main()
   	{
   		Func<int, int, int> f = delegate(int a, int b){
   			return a+b;
   		};
   		
   		int a = f(1,2);	
   		Console.Write(a);		// 3
   	}
   }
   ```

   

   

   g. Can be used with Lambda Expressions

   ```c#
   using System;
   					
   public class Program
   {
   	public static int Add(int a, int b){
   		return a+b;
   	}
   	
   	public static void Main()
   	{
   		Func<int, int, int> f = (a, b) => (a+b);
   		int a = f(1,2);
   		Console.Write(a);		// 3
   }
   ```

   



