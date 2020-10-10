# 1. C# Fundamentals



1. #### **What are Identifiers in C#?**

   ​	a. Identifiers are name of the user defined classes, methods, variables etc.

   ​	b. It is used to identify user defined code.



2. #### What is a Data Type in C#?

   It specifies the type of data, a valid C# variable can hold.



3. #### **What data types are present in C#?**

   ​	a. Value Data Type

   ​	b. Reference Data Type

   ​	c. Pointer Data Type



4. #### **What is Value Data Type?**

   ​	a. It will directly store the variable in memory.

   ​	b. Stored in Stack Memory

   ​	c. Different types are:

   ​			a. **Int** (32 bit)	-	Default = 0

   ​			b. **Long** (64 bit)	-	Default = 0

   ​			c. **Byte** (8 bit)	-	Default = 0

   ​			d. **Float** (32 bit)	-	7 digit precision	-	Default  = 0.0F

   ```C#
   		float x = 3.45F;	// If suffix f/F is not used, then it is treated as double
   ```

   ​			e. **Double** (64 bit)	-	14-15 digit precision	-	Default = 0.0D

   ```c#
   		double x = 3.45d;	// suffix d/D is optional
   ```

   ​			f. **Decimal** (128 bit)	-	28-29 digit precision	-	Default = 0.0M

   ```c#
   		decimal x = 3.45m;	// If suffix m/M is not used, then it is treated as double
   ```

   ​			g. **Char** (16 bit)	-	Store single character	-	Default '\0'

   ​			h. **Bool**	-	Store either true/false	-	Default = false



5. #### What is Reference Data Type?

   ​	a. This variable contains the memory address of variable storing the value.

   ​	b. The variable is stored in Stack Memory, the value is stored in Heap memory.

   ​	c. Types are:

   ​			a. **String**

   ​			b. **Object** (Base class for all data types in C#)



6. #### What is Pointer Data Type?

   ​	a. It contains the a memory address of the variable value.

   ```c#
   // Declare a variable
   int n = 10;
   
   // Store location of variable n in pointer variable p
   int* p = &n;
   ```

   

7. #### What are variables and to initialize them?

   ​	a. Variable is a placeholder for storing data.

   ​	b. It can be initialize in two ways:

   ​			a. Compile Time 

   ```c#
   int n = 10;
   ```

   ​			b. Run Time

   ```c#
   int n = Convert.ToInt32(Console.ReadLine());
   ```

   

8. #### What is String Interpolation in C#?

   ​	a. It is a better way to concatenate strings.

   ​	b. It is represented as $"";

   ```c#
   string firstName = "Prajwal";
   string lastName = "Sharma";
   string employeeID = 12345;
   
   string employeeDetails = $"Mr. {firstName} {lastName} ({employeeID})"; // Mr. Prajwal Sharma (12345)
   ```





# 2. Var & Dynamic



1. #### What is ***var*** keyword in C#?

   ​	a. It is implicitly typed local variable.

   ​	b. It is declared without specifying any C# data type.

   ​	c. It is mostly used in LINQ

   ​	d. It's scope is local, therefore it cannot be defined in a class or can be passed to another method.

   ​	e. It should be initialized at time of declaration.

   ​	f. It cannot store null

   ```c#
   var a = "Hello";	// Valid
   
   var b;			// Invalid
   
   var c = null;	// Invalid
   ```

   

2. #### What is *dynamic* keyword in C#?

   ​	a. This data type is used to avoid compile-time type checking.

   ​	b. It is initialized at run-time.

   ```c#
   dynamic	a = "Hello";
   ```

   ​	c. It can be passed to any method (kind of polymorphism)

   ```c#
   public void Fun(dynamic a, dynamic b){
       Console.Write(a+b);
   }
   
   public static void Main(){
       Fun("Hello", "World");		// HelloWorld
       Fun("Hello", 1);			// Hello1
       Fun(1,3);					// 4
   }
   ```

   

3. #### What are the difference between var & dynamic?

   | Var                                        | Dynamic                                |
   | :----------------------------------------- | -------------------------------------- |
   | ***var*** keyword is used                  | ***dynamic*** keyword is used          |
   | data type is checked at ***compile time*** | data type is checked at ***run-time*** |
   | It should be initialized when declared     | It can be initialized later            |

   

# 3. Access Modifiers



1. #### **What are the different access modifiers present in C#?**

   ​	a. ***Public***	-	Can be accessed anywhere in a program

   ​	b. ***Private***	-	Can be accessed from current class only

   ​	c. ***Protected***	-	Can be accessed from current class or derived classes

   ​	d. ***Internal***	-	Can be accessed from classes present in same namespace (assembly) (Default in C#)

   ​	e. ***Private Protected***	-	Can be accessed from same class or derived classes within same namespace

   ​	f. ***Protected Internal***	-	Can be accessed from derived classes in same namespace





# 4. Boxing & Unboxing



1. #### What is Boxing?

   ​	a. Process of converting Value Data Type to Reference Data Type.

   ​	b. Implicit Conversation (Automatic)

   ​	c. Value stored in ***Stack*** memory copies to ***Heap*** memory

   ```c#
   int num = 23;		// 23 - Value Type
   Object obj = num;	// 23 - Implicit Conversion - Reference Type
   
   num = 30;
   
   Console.Write(num);	// 30
   Console.Write(obj)	// 23	-	It copies the value to Heap
   ```

   

2. #### What is Unboxing?

   ​	a. Process of converting Reference Type to Value Type.

   ​	b. It is explicit conversion (Manual)

   ​	c. Object stored in ***Heap*** memory copies to ***Stack*** memory

   ```c#
   int num = 100;
   Object obj = num;		// Boxing
   int i = (int) obj;		// Unboxing
   ```

   

# 5. Params



1. What is Params keyword in C#?

   ​	a. It is a keyword in C# through which we can take variable number of arguments in a function.

   ​	b. Used when we don't know how much arguments be passed in our function.

   ​	c. Only 1 params is allowed in function.

   ​	d. Length of params array will be 0 if no argument is passed.

   ```c#
   public void Fun(params int[] myArguments){
       foreach(int i in myArguments){
           Console.Write(i+" ");
       }
   }
   
   public void Main(){
       Fun(1,2,3,4,5,6);	// 1 2 3 4 5 6 
   }
   ```

   e. We can also send different type of parameters in params

   ```c#
   public void Fun(params object[] array){
       foreach(object obj in array){
           Console.Write(obj + "-");
       }
   }
   
   public void Main(){
       Fun("Hello", 1, "World", 2.5);	// Hello-1-World-2.5
   }
   ```

   

   # 6. Nullable Types



1. #### What is Nullable Type in C#?

   ​	a. C# does not allow us to assign null value to a value type variable.

   ​	b. Nullable types is a special feature in C# that allow us to store null value in variable

   ​	c. It can be declared in two ways:

   ```c#
   int j = null;		// Error
   
   Nullable<int> j = null;		// Valid
   
   int? j = null;		// Valid
   ```

   

2. #### How to access Nullable Type variables?

   ​	a. ***GetValueOrDefault***()

   ​	b. ***Directly***

   ​	c. ***Value*** Property

   ​	d. ***HasValue*** Property

   ```c#
   int? a = null;
   
   a.GetValueOrDefault();		// 0 - Default value if null is assigned
   
   a = 30;
   
   a.GetValueOrDefault();		// 30
   a.Value;					// 30
   a.HasValue;					// true
   
   a = null;
   a.Value;		// Error
   a.HasValue;		// false
   
   Console.Write(a);		// Blank
   ```

   
   #### 3. What is Null-Coalescing Operator (??) in C#?

   ​	a. It is used to minimize run time errors because of null values.

   ```c#
   int? a = null;		// Assign null
   
   int	b	= a ?? 3;	// Assign 3 if a is null
   ```

   

4. #### What is the use of nullable types?

   ​	a. Main use is in DB applications, if a column requires null value then we can send null from C# code.

   ​	b. It can also store undefined values.

   ​	c. We can use nullable types instead of reference types for storing null.



# 7. Structures



1. #### What is a Structure in C#?

   ​	a. User defined data type used to store collection of different data types.

   ​	b. It is Value Type.

   ​	c. Stored in Stack.

   ​	d. Used when we need to create our own data type

   ```c#
   public struct Person{
       public string Name;
       public int Age;
       public int Weight;
   }
   
   public class PersonClass{
       public void Main(){
           Person p1;	// Structure Declaration
           p1.Name = "Prajwal Sharma";
           p1.Age = 25;
           p1.Weight = 80;
           
           Console.WriteLine(p1.Name);		// Prajwal Sharma
           Console.WriteLine(p1.Age);		// 25
           Console.WriteLine(p1.Weight);	// 80
       }
   }
   ```

   

2. #### What is Nested Structures?

   We can declare one structure in another structure, that is called nesting of structures.

   ```c#
   public struct Address{
       public string City;
       public string State;
   }
   
   public struct Person{
       public string Name;
       public Address a1;		// Nesting of Structure
   }
   
   public class MyClass{
       public static void Main(){
           Person p;
           p.Name = "Prajwal";
           p.a1.City = "Pune";
           p.a1.State = "Maharashtra";
           
           Console.Write(p.Name);		// Prajwal
           Console.Write(p.a1.City);	// Pune
           Console.Write(p.a1.State);	// Maharashtra
       }
   }
   ```



3. #### What are the differences between Structure & Class?

   | Structure                        | Class                                |
   | -------------------------------- | ------------------------------------ |
   | Value Type                       | Reference Type                       |
   | Inheritance not supported        | Inheritance is supported             |
   | Copies the value while assigning | Copies the reference while assigning |

   

# 8. Is & As



1. #### What is "Is" keyword in C#?

   a. This keyword is used to check the object type at run time.

   b. It returns bool value

   c. It is used to reduce Invalid Cast Exceptions.

   ```c#
   class c1{
       
   }
   
   class c2{
       
   }
   
   class MyClass{
       public void Test(object obj){
           bool a = obj is c1;			// True/False
           bool b = obj is c2;			// True/False
       }
   }
   ```

   

2. #### What is "as" keyword in C#?

   a. It works same as "is" keyword, but instead of returning bool value, it returns the object.

   b. If object is campatible, then returns the object, else return null.

   ```c#
   object o1 = new Class1();
   object o2 = 5;
   object o3 = "Hello";
   object o4 = null;
   
   string s1 = o1 as string;		// null
   s1 = o2 as string;				// null
   s1 = 03 as string;				// Hello
   s1 = o4 as string;				// null
   ```

   

3. #### **What should we use, "is" or "as"?**

   We should use "as" keyword because we can achieve the result in just 1 line. "is" keyword first check the compatibility, then we convert the object.



# 9. Ref & Out



1. #### What is "out" keyword in C#?

   ​	a. It is used to pass arguments to a method as reference type.

   ​	b. It is used to return multiple values from a method.

   ​	c. It is ***not mandatory*** to initialize an out variable before passing to method.

   ​	d. It is ***mandatory*** to initialize out variable in the called method.

   ```c#
   public void Add(out int num){
       num = 10;						// Mandatory Initialization
       num += 10;
   }
   
   public static void Main(){
       int num;
       Add(out num);
       Console.Write(num);				// 20
   }
   ```

   [^Single]: Return single value from a function

   

   ```c#
   public void Add(out int a, out int b, out int c){
       a = 10;
       b = 20;
       c = 30;
       
       a += 10;
       b += 20;
       c += 30;
   }
   
   public static void Main(){
       int a;
       int b;
       int c;
       
       Add(out a, out b, out c);
       
       Console.Write(a);	// 20
       COnsole.Write(b);	// 40
       Cosnole.Write(c);	// 60
   }
   ```

   [^Multiple]: Return Multiple Values from a function

   

2. #### C# 7 features for out parameter?

   ​	a. We can declare variables while calling method.

   ​	b. out parameter can be used with var keyword.

   ​	c. Parameter names can be different

   ```c#
   public void Area(out int l, out int b, out int area){
       l = 10;
       b = 10;
       area = l * b;
   }
   
   public static Void Main(){
       Area(out int length, out int breadth, out int area);
       Console.Write(length);	// 10
       Console.Write(breadth);	// 10
       Console.Write(area);	// 100
   }
   ```

   

3. #### What is "Ref" keyword in C#?

   ​	a. It is used to pass variable as reference to a method.

   ​	b. It is mandatory to initialize the variable before passing to a method.

   ```c#
   int b = 10;
   
   Add(ref 10);
   Console.Write(b);		// 5
   
   void Add(ref in b){
       b = 5;
   }
   ```

   

4. #### What are the differences between "Ref" & "Out"?

| Ref                                                    | Out                                                |
| ------------------------------------------------------ | -------------------------------------------------- |
| Mandatory to initialize before passing                 | Not mandatory to initialize before passing         |
| Not mandatory to initialize variable in passing method | Mandatory to initialize variable in passing method |
| Data pass is bi-directional                            | data pass is uni-directional                       |



# 10. Const & Readonly



1. #### What are the differences between "*const*" & "*readonly*" in C#?

| Readonly                                                  | Const                                 |
| --------------------------------------------------------- | ------------------------------------- |
| **readonly** keyword is used                              | **const** keyword is used             |
| It is a run-time constant                                 | It is a compile-time constant         |
| value can be assigned while declaration or in Constructor | value is assigned only at declaration |
| Cannot be declared in a method                            | Can be declared in a method           |







































