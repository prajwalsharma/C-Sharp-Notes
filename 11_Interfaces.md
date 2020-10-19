# 1. Interfaces



1. #### What is an Interface?

   a. It is a fully un-implemented/pure-abstract class.

   b. It can have methods & properties like classes.

   c. It contains only the declaration of the methods, the implementation of these methods will be provided by the class who's 	implementing the interface.



2. #### What are the features of an Interface?

   a. Interface specify what a class must do and not how.

   b. Interface cannot have private members.

   c. By default all members are private & abstract.

   d. Multiple inheritance can be achieved through interfaces.

   ```c#
   // Interface
   interface IAnimal{
       void Walk();
   }
   
   // Class implementing an interface
   public class Dog : IAnimal{
       void Walk(){
         Console.Write("Dog is walking");  
       }
   }
   ```



3. #### What are the advantages of Interface?

   a. It is used to achieve loose coupling.

   b. It is used to achieve total abstraction.

   c. It is used to achieve multiple inheritance.



4. #### Why do we need interface when we have Abstract class?

   Multiple inheritance cannot be achieved through Abstract classes. It can only be supported through interfaces.



5. #### What are the different types of Inheritance?

   a. **Implementation Interface**

   ​	Class inheriting from another class

   b. **Interface Inheritance**

   ​	Class inheriting from an Interface



6. #### Common Interview Questions?

   a. Interfaces are **public** by default

   b. Interface ***cannot*** implement ***Abstract*** Class, but abstract class can implement an interface.

   c. Interface cannot be declared ***sealed***

   d. A class can implement more than 1 interface.

   e. For ***normal*** class, it is ***mandatory*** to implement all methods of interface.

   f. For ***Abstract*** class, it is ***not mandatory*** to implement all methods of interface.



7. #### How is Interface different from a class?

   a. We cannot create an object of Interface.

   b. Interface does not contain constructors.

   c. Interface cannot be sealed.

   d. An Interface can inherit multiple interfaces.

   e. All methods in an interface are public & abstract.



8. #### What are the similarities between Abstract Class & Interface?

   a. Both interface & abstract class cannot be initialized.

   b. Both contain abstract methods.

   c. Both cannot be declared sealed.



9. #### What is the difference between Abstract Class & Interface?

   a. In interface all methods are abstract methods **(Fully Unimplemented)**. In Abstract class, not all methods can be abstract methods, it can contain concrete methods as well **(Partially Implemented)**

   b. ***Interfaces*** can be used for ***multiple inheritance***, Abstract class cannot.

   c. ***abstract*** keyword is not required in Interface, it is required in Abstract classes.

   ```c#
   // Interface 1
   interface A{
       void Method1();
       void Method2();
   }
   
   // Interface 2
   interface B {
       void Method3();
   }
   
   // Class implementing interface
   public class MyClass : B {
       public void Method1(){
         // Method1 Implemented  
       }
       
       public void Method2(){
           // Method2 Implemented
       }
       
       public void Method3(){
           // Method3 Implemented
       }
   }
   
   class Program{
       public static void Main(){
           MyClass mc = new MyClass();
           mc.Method1();
           mc.Method2();
           mc.Method3();
       }
   }
   ```

   ```c#
   // Interface
   public interface IArea{
       void GetArea(double a, double b);
   }
   
   // Class implementing Interface
   public class Rectangle : IArea{
       public void GetArea(double a, double b){
           Console.Write(a*b);
       }
   }
   
   // Class implementing Interface
   public class Circle : IArea{
       public void GetArea(double a, double b){
           Console.Write(Math.PI * a * a);
       }
   }
   
   IArea a = new Rectangle();
   a.GetArea(3,4);	// 12
   
   a = new Circle(3,3);	// 143
   ```





10. #### What is multiple Inheritance?

    Class inheriting from multiple interfaces 

    ```c#
    public interface A {
        void Display(string interfaceName);
    }
    
    public interface B {
        void Display(string interfaceName);
    }
    
    class MyClass : A,B {
        
        public void Display(string interfaceName){
            Console.Write(interfaceName + " method is implemented");
        }
        
    }
    
    MyClass c = new MyClass();
    c.Display("No Interface");	// Display method is implemented
    
    A a = new MyClass();
    a.Display("A");				// A method is implemented
    
    B b = new MyClass();
    b.Display("B");				// B method is implemented
    ```

    [^Implicit]: Implicit Interface Implementation

    ```c#
    public interface A {
        void Display();
    }
    
    public interface B{
        void Display();
    }
    
    public class C : A,B {
        public void A.Display(){
            Console.Write("Hello from Interface A");
        }
        
        public void B.Display(){
            Console.Write("Hello from Interface B");
        }
    }
    
    C c = new C();
    c.Display();	// Error
    (A)c.Display();	// Hello from Interface A
    (B)c.Display();	// Hello from Interface B
    
    A a = new C();
    a.Display();	// Hello from Interface A
    
    B b = new C();
    b.Display();	// Hello from Interface B
    ```



11. #### When to use Abstract Class & when to use Interface?

    a. Use abstract class when there is such implementation that'll be common for all classes, thus avoiding code duplication.

    b. Use Interfaces when each class require different implementation for same method.