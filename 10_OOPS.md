# 1. Class & Object



1. #### What is a Class?

   a. It is a user-defined data type (blueprint) from which objects are created.

   b. It consists of fields & Methods

   c. Example, Mobile is a class, Laptop is a class, Animal is a class, Employee is a class



2. #### How to declare a class?

   ```c#
   // Simple
   public class Animal{
       
   }
   
   // Inheritance from a base class
   public class Dog : Animal{
       
   }
   
   // Inheritance from an Interface
   public class Cat : IAnimal{
       
   }
   ```

   

3. #### What are the components of a Class?

   a. **Constructor**

   ​	Used to initialize new objects

   b. **Field**

   ​	Used to provide a state/property of the class and its objects

   c. **Method**

   ​	Used to implement behaviour of the class

   ```c#
   public class Animal{
       
       // Field
       public string color;
       
       // Constructor
       public Animal(){
           this.color = "Not Defined";
       }
       
       // Method
       public void GetLegs(){
           Console.Write(4);
       }
       
   }
   ```

   

4. #### What is Object?

   a. It is a basic unit of a class that represents a real world entity.

   b. Every object has some **state**, **behaviour** & **Identity**.

   ```c#
   // Identity - Name of the object
   Animal dog = new Animal();
   
   // State
   dog.Breed;
   dog.Color;
   
   // Behaviour
   dog.Bark();
   dog.Run();
   dog.GetLegs();
   ```

   

5. #### How to declare objects of a class?

   a. Creating an object is called instantiation of class.

   b. All the objects share the states & behaviours of the class.

   c. The values of each state is different for each object.

   d. A single class can have any number of objects.

   ```c#
   public class Dog{
       string color;
       string breed;
       int age;
       
       void Bark(){
           
       }
       
       void Sleep(){
           
       }
   }
   
   Dog dog1 = new Dog();
   Dog dog2 = new Dog();
   
   dog1.color = "Red";
   dog2.color = "Black";
   
   dog1.Bark();
   dog2.Bark();
   ```

   

6. When creating an object, when will the memory be allocated?

   ```c#
   Dog tommy;	// Its value will be null, no memory is allocated
   
   Dog tommy = new Dog();	// new keyword allocates the memory for the new object
   ```






# 2. Constructors



1. #### What is a Constructor?

   a. A special method of a class which is automatically invoked whenever an object of the class is created.

   b. It is used to assign initial values to the data members.



2. #### What are the properties of Constructor?

   a. Name of constructor should be **same** as Class name.

   b. Constructor don't have a **return** **type**.

   c. Class can have **any** number of constructors

   d. Class can have only **one** static constructor

   e. Static constructor **cannot** be **parameterized** constructor.



3. #### What are the types of Constructors?

   There are 5 type of constructors:

   ​	a. **Default** Constructor

   ​	b. **Parameterized** Constructor

   ​	c. **Copy** Constructor

   ​	d. **Static** Constructor

   ​	e. **Private** Constructor



4. #### What is a Default Constructor?

   a. Constructor having no parameters.

   b. It is created internally by the compiler by default if you don't create it explicitly.

   c. Assigns all value types to 0, and all reference types to null, false for Boolean.

   ```c#
   public class Dog{
       public Dog(){
           Console.Write("Default Constructor is called");
       }
   }
   
   Dog dog = new Dog();
   ```

   

5. #### What is a Parameterized Constructor?

   a. Constructor with 1 or more parameters.

   b. It initialize every object with different values

   ```c#
   public class Dog(){
   	public Dog(string name){
           Console.Write("Parametrized Constructor is called for dog: " + name);
       }
   }
   
   Dog dog = new Dog("Tony");
   ```

   

6. #### What is Copy Constructor?

   a. Constructor that initialize instance from other instance.

   ```c#
   public class Dog(){
       
       string breed;
       
       public Dog(){
           this.breed = "Labra";
       }
       
       public Dog(Dog labra){
           this.breed = labra.breed;
       }
   }
   
   Dog dog = new Dog();
   Dog dog2 = new Dog(dog);
   ```

   

7. #### What is a Private Constructor?

   a. A constructor with private access modifier is called private constructor.

   b. If a class has private constructor, then object cannot be created of that class.

   c. If a class has private constructor, then no other class can be derived from this class.

   d. Use private constructor when our class is non static, but all methods are static.

   e. It is used in singleton class pattern.

   ```c#
   public class Number{
       private Number(){
           // Private Constructor
       }
       
       public static int count;
       
       public static int GetCount(){
           return ++count;
       }
       
   }
   
   Number num = new Number();	// Error
   
   Number.count = 20;
   Number.GetCount();	// 21
   ```



8. #### What is Static Constructor?

   a. This constructor is used to instantiate static fields.

   b. Only one static constructor can be created in a class.

   c. This constructor is called only once.

   d. It is automatically called before the first instance is created, or any static member is referenced.

   ```c#
   public class Dog{
       
       public static int count = 30;
       
       static Dog(){
           Console.Write("Static Constructor is called");
       }
       
       public Dog(){
           Console.Write("Default constructor is called");
       }
       
   }
   
   // Method 1
   Dog dog = new Dog();	// Static Constructor is called
   						// Default Constructor is called
   
   // Method 2
   Console.Write(Dog.count);	// Static Constructor is called
   							// 30
   
   ```

   



# 3. Inheritance



1. #### What is Inheritance?

   Feature of OOP that allows a class to inherit features of another class.



2. #### What is the use of Inheritance?

   a. Inheritance is used to achieve ***reusability***.

   b. If we already have a class that has fields & methods that we need in our new class, we can derive our new class from that 	base class.

   ```c#
   using System;
   					
   public class Program
   {
   	public static void Main()
   	{
   		Dog dog = new Dog();			// Base class constructor is called
   										// Derived class Constructor is called
   		dog.GetAnimalName("Tommy");		// Hello, Tommy
   	}
   }
   
   public class Animal{
   	
   	public Animal(){
   		Console.WriteLine("Base class constructor is called");
   	}
   	
   	public void GetAnimalName(string name){
   		Console.WriteLine("Hello, " + name);
   	}
   	
   }
   
   public class Dog : Animal{
   	public Dog(){
   		Console.WriteLine("Derived class Constructor is called");
   	}
   }
   ```

   

3. #### What are the types of Inheritance?

   a. **Single Inheritance**

   ​	One class inheriting from one class.

   

   b. **Multilevel Inheritance**

   ​	Once class is inheriting from another class, that another class is inheriting from some other class.

   

   c. **Hierarchical Inheritance**

   ​	Multiple classes are inheriting from a single base class forming an hierarchy.

   

   d. **Multiple Inheritance (Through Interfaces)**

   ​	One class inheriting from multiple classes. This is not allowed using classes, but allowed with interfaces.

   

   e. **Hybrid Inheritance**

   ​	Mix of above mentioned inheritance

<img src="https://media.geeksforgeeks.org/wp-content/uploads/Single.jpg" alt="img" style="zoom: 50%;" /><img src="https://media.geeksforgeeks.org/wp-content/cdn-uploads/multilevel-inheritance.jpg" alt="img" style="zoom: 50%;" /><img src="https://media.geeksforgeeks.org/wp-content/uploads/Hierarchical.jpg" alt="img" style="zoom:33%;" /><img src="https://media.geeksforgeeks.org/wp-content/uploads/Multiple-1.jpg" alt="img" style="zoom: 50%;" /><img src="https://media.geeksforgeeks.org/wp-content/uploads/Hybrid.jpg" alt="img" style="zoom:33%;" />



4. #### Important facts for Inheritance?

   a. A superclass can have any number of subclasses.

   b. A subclass can heave only one superclass.

   c. Constructors are not inherited to base class, but can be invoked by derived class.

   d. Private fields of base class cannot be accessed directly by derived class, but can be done if properties are there.





# 4. Encapsulation



1. #### What is Encapsulation?

   a. It is the feature of wrapping data under a single unit.

   b. It is a mechanism that binds together the code and the data it manipulates.

   c. It is used to protect data from being accessed from outside.



2. #### What is Data Hiding?

   The hiding of class data (variables) from other classes is called Data Hiding.

   It is achieved through encapsulation



3. #### How to achieve Encapsulation?

   a. By declaring all the variables as private.

   b. By using Properties in class to get/set those variables.

   ```c#
   public class Program
   {
   	public static void Main()
   	{
   		Encapsulation cap = new Encapsulation();
   		
   		cap.Age = 20;
   		Console.WriteLine(cap.Age);		// 20
   		
   		cap.Name = "Prajwal";
   		Console.WriteLine(cap.Name);	// Prajwal
   	}
   }
   
   public class Encapsulation{
   	
       // Step 1: Make variables private
   	private int _age;
   	private string _name;
   	
       // Step 2: Use properties to get/set variables
   	public int Age{
   		get{
   			return _age;
   		}
   		set{
   			_age = value;
   		}
   	}
   	
   	public string Name{
   		get{
   			return _name;
   		}
   		set{
   			_name = value;
   		}
   	}
   	
   }
   ```

   

4. #### What are the benefits of encapsulation?

   a. **Data Hiding**

   ​	The calling class has no idea about the implementation of the class.

   ​	The calling class cannot directly access the variables.

   

   b. **Flexibility**

   ​	We can make our class read-only by removing set method, and write-only by removing get method.

   c. **Reusability & Testing**





# 5. Abstraction



1. #### What is Abstraction?

   The process of showing only necessary things to the outside world and hiding unnecessary things is called Abstraction.



2. #### Example of Abstraction?

   a. **ATM Machine**

   ​	We don't know how it's working internally, we're shown only the UI & buttons to withdraw money.

   b. **Mobile Phone**

   ​	We don't know how it's making calls internally, we're shown only the UI to call someone.



3. #### How to achieve Abstraction?

   a. Using Abstract Classes

   b. Using Abstract Methods



4. #### What is an Abstract Class?

   a. It is class declared with "***abstract***" keyword.

   b. Abstract class consists both **abstract** & **non abstract** methods.

   c. We cannot create an **object** of abstract class.

   d. Abstract class with all abstract methods is called **Pure Abstract Base Class.**

   e. Abstract class with both abstract & non-abstract methods is called **Abstract Base Class.**

   f. Abstract methods can only be created in **Abstract** classes.

   g. We cannot declare abstract class as **Sealed** class.



5. #### What is the use of Abstract Class?

   a. It is used in scenarios where we want to define a superclass that have both abstract methods & non-abstract methods.

   b. The abstract methods are just generalized methods that each subclass will implement according to it's need.

   c. The non-abstract methods are the one that'll be universally same for all derived classes.

   d. Real World Example:

   ```
   We have an application that handle orders having order types:
   
   1. Store Order
   2. Factory Order
   3. Online Order
   
   The order handling method is different for different order, but order cancelling method is same for every order.
   
   Solution 1:
   	If we create everything in 1 class then it will break SOLID principles.
   	
   Solution 2:
   	We will create an abstract class having non-abstract method "Order Cancellation" and all other 			methods will be abstract that derived classes will implement as per the requirement.
   ```

   ```c#
   //Abstract Base Class
   public abstract class Orders{
       
       int orderId;
       datetime createdOn;
       double amount;
       
       // Abstract methods that will iplemented by derived classes
       public abstract void ValidateOrder();
       public abstract void ProcessOrder();
       
       // Common for all derived classes
       public void CancelOrder(){
           Console.Write("Order is Cancelled");
       }
       
   }
   
   // Store Order Class
   public class StoreOrder : Order{
       
       int storeId;
       
       public override void ValidateOrder(){
           Console.Write("Validation for Store Order");
       }
       
       public override void ProcessOrder(){
           Console.Write("Process store Order");
       }
       
   }
   
   
   ```

   [Real World Example](https://www.codebyamir.com/blog/when-to-use-an-abstract-class-in-java)















