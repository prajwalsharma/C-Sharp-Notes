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

   

































































