# 1. Methods



1. #### What is a method in C#?

   ​	a. It is a block of code that can be reused.

   ​	b. It provides reusability, readability & maintainability.

   

2. #### What are the component of a Method?

   ​	***a. Access Modifier***

   ​		Defines the access type of the method (public, private etc)

   ​	***b. Return Type*** 

   ​		Defines the data type returned by the method.

   ​	***c. Name***

   ​		Defines the name of the method, user will call this method using it's name

   ​	***d. Parameters***

   ​		Defines the parameters passed to this method.

   ​	***e. Method Body***

   ​		Block of code



3. #### **What is a method Signature?**

   It is defined by 2 parameters:

   ​	a. Method Name

   ​	b. Parameter List (Number, data type & order of parameters)

   





# 2. Method Overloading



1. #### **What is Method Overloading?**

   Method overloading means, defining multiple methods with same name but with different signature.



2. #### What are the necessary conditions to do method overloading?

   ​	a. Number of Parameters should be different

   ​	b. Order of parameters should be different

   ​	c. Data Type of parameters should be different.

   ​	d. ***Return type*** of the method is not considered

   ```c#
   public int Add(int a, int b){				// Valid
       return a+b;	
   }
   
   public int Add(int a, int b, int c){		// Valid - No. of parameters
       return a+b+c;
   }
   
   public string Add(string a, string b){		// Valid - Data type of parameters
       return a+b;
   }
   
   public string Add (int a, string b){		// Valid - Order of parameters
       return a+b;
   }
   
   public void Add(int a, int b){				// Invalid
       Console.Write(a+b);
   }
   ```

   

3. #### Why do we need Method Overloading?

   When we need to perform same task, but for different inputs.







# 3. Method Parameters



1. #### What are the different type of method parameters in C#?

   ​	***a. Named Parameters***

   ​	***b. Ref***

   ​	***c. Out***

   ​	***d. Default or Optional***

   ​	***e. Dynamic***

   ​	***f. Value***

   ​	***g. Params***

   ```c#
   void Fun(string s1, string s2, string s3){}
   
   Fun(s3: "World", s2: "-", s1: "Hello");
   ```

   [^Named]: Named Parameters in a method

   ```c#
   void Fun(ref int a){}
   int a = 10;
   Fun(ref a);
   ```

   [^Ref]: Ref Parameter in a method

   ```c#
   void Fun(out int a){}
   Fun(out int a);
   ```

   [^Out]: Out Parameter in a method

   ```c#
   void Fun(string name, int id, string bloodGroup = "A+", string department = "Default"){}
   Fun("Prajwal", 3);
   Fun("Prajwal", 2, "B+");
   Fun("Prajwal", 2, "B+", "Accounts");
   ```

   [^Optional]: Default or Optional Parameters in a method

   ```c#
   void Fun(dynamic a){}
   Fun(4);
   Fun("Hello");
   ```

   [^Dynamic]: Dynamic Parameter in a method

   ```c#
   Fun(int a, int b){}
   Fun(4,5);
   ```

   [^Value/Normal]: Value Parameters in a method

   ```c#
   Fun(params int[] arrray){}
   Fun(1,2,3,4,5,6,7,8,9,10);
   ```

   [^Params]: Params in a method

   





# 4. Method Overriding (Run-time Polymorphism)



1. #### What is Method Overriding in C#?

   Creating a method in derived class with same signature as method in a base class is called method overriding.

   ```c#
   public class Animal{
       public void Move(){
           Console.Write("Animal Moves");
       }
   }
   
   public class Dog : Animal{
       public void Move(){					// Overriding parent class method
           Console.Write("Dog Moves");
       }
   }
   
   public class MyClass{
       new public static void Main(){
           
           Animal labra = new Animal();
           labra.Move();					// Animal Moves
           
           labra = new Dog();
           labra.Move();					// Animal Moves - Problem using new keyword, this will be 												// resolved by using virtual & override
       }
   }
   ```

   [^new keyword]: Method Overriding without virtual & override keywords

   

2. #### Which Keywords are used to for Method Overriding in C#?

   ​	a. Virtual

   ​	b. Override

   ​	c. Base

   ​	d. New
   
   ```c#
   public class Animal{
       public virtual void Move(){
           Console.Write("Animal Moves");
       }
   }
   
   public class Dog : Animal{
       public override void Move(){		// Overriding parent class method
           Console.Write("Dog Moves");
       }
   }
   
   public class MyClass{
       new public static void Main(){
           
           Animal labra = new Animal();
           labra.Move();					// Animal Moves
           
           labra = new Dog();
           labra.Move();					// Dog Moves - Problem solved										
       }
   }
   ```
   
   [^Method Overriding]: Using Virtual & Override keywords	
   
   
   
   ```c#
   public class Animal{
       public virtual void Move(){
           Console.Write("Animal Moves");
       }
   }
   
   public class Dog : Animal{
       public override void Move(){		// Overriding parent class method
           base.Move();					// Animal Moves
           Console.Write("Dog Moves");
       }
   }
   
   public class MyClass{
       new public static void Main(){
           
           Dog labra = new Dog();
           labra.Move();					// Dog Moves
     							
       }
   }
   ```
   
   [^Method Overriding]: Using base keyword for invoking Base class methods
   
   

3. #### How to invoke Base class constructor using "base" keyword?

   Using "Base" keyword, we can call base class constructor internally.

   ```c#
   public class Animal{
       public Animal(){
           Console.Write("Base class default construcotr is called");
       }
       
       public Animal(int i, int j){
           Console.Write("Base class parmeterized constructor is called");
       }
   }
   
   public class Dog : Animal{
       public Dog() : base(){};					// Invoke base class default constructor
       public Dog(int i, int j) : base(i,j) {};	// Invoke base class parameter constructor
   }
   ```

   





# 5. Method Hiding/Shadowing



1. #### What is Method Hiding?

   Process of hiding method of base class from derived class is called Method Hiding.

   ```c#
   public class Animal{
       public void Move(){
           
       }
   }
   
   public class Dog : Animal{
       public new void Move(){		// Hide base class method using "new" keyword
           
       }
   }
   ```

   

2. #### How to invoke base class methods in Method Hiding?

   There are three ways to call base class methods:

   ​		a. base keyword

   ​		b. Type Casting derived class object

   ​		c. Using parent class reference

   ```c#
   // Using base keyword
   base.Move();			// Animal is moving
   
   // Using TypeCasting
   Dog dog = new Dog();
   (Animal)dog.Move();		// Animal is moving
   
   // Using base class reference
   Animal dog = new Dog();
   dog.Move();				// Animal is moving
   ```

   

3. #### What are the difference between Method Hiding & Method Overriding?

   ​	a. Method Hiding is used to hide base class methods, Method overriding is used to redefine base class methods.

   ​	b. Method hiding use "***new***" keyword, Method overriding use "***virtual***" & "***override***" keywords.





# 6. Partial Method



1. #### What is a Partial Method in C#?

   Special Method in which method declaration is in one partial class & definition is in other partial class or both can be in same class.

   ​	a. It can return only void data type

   ​	b. ref keyword can be used, out cannot be used

   ​	c. Can only be created in partial class.

   ```c#
   public partial class Class1{
       public void Fun(int a);
   }
   
   public partial class Class2{
       public void Fun(int a){
           Console.Write(a);
       }
   }
   ```

   



# 7. Extension Method



1. #### What is extension method in C#?

   ​	a. Special methods that can be added in a class without changing original class's source code.

   ​	b. Used when you have a original class, which is either sealed or not accessible and you want to add more methods in it, 		then you can create extension methods.

   ​	c. These methods are always defined in static class.

   ​	d. Extension method doesn't support method overriding.

   ​	e. "this Animal obj" is called ***Binding Parameters***

   ```c#
   // Original class
   public sealed class Animal{
       public void GetType(){
           
       }
       
       public void GetLegs(){
           
       }
   }
   
   // Extension method static class
   public static class AnimalExtension{
       public static void GetColor(this Animal obj, string s){
           Console.Write("Color of animal {0} is Black", s);
       }
   }
   
   // Driver Class
   public class MyClass{
       public static void Main(){
           Animal dog = new Animal();
           dog.GetColor("Labrador");		// Color of animal Labrador is Black
       }
   }
   ```

   



2. #### What are the advantages of using Extension Method?

   ​	a. We can add new methods in existing classes without using Inheritance or changing original class code.

   ​	b. We can add methods in Sealed classes.





# 8. Local Functions



1. #### What are Local Functions in C#?

   ​	a. Functions defined inside a function are called Local Functions (Nested Functions)

   ​	b. These methods are private by default, we cannot specify access modifiers

   ​	c. Overloading is not allowed

   ​	d. Static functions are not allowed

   ```c#
   public static void Main(){
       
       int x = 10;
       int y = 20;
       
       void Fun(int z){
           Console.Write(x);		// 10
           Console.Write(y);		// 20
           Console.Write(z);		// 30
       }
       
       Fun(30);
       
   }
   ```

   

2. #### What are the advantages of Local Functions?

   ​	a. Used to create local Generic Functions

   ```c#
   public static void Main(){
   	void MyMethod<T>(T value){
           Console.Write(value);
       }
       
       MyMethod<int>(5);		// 5
       MyMethod<string>("Hello")	// Hello
   }
   ```

   







