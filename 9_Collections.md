# 1. Collections



1. #### What are Collections in C#?

   ​	a. It contains set of classes to contain elements in a generalized manner.

   ​	b. We can store, update, insert, search sort elements in collections.

   ​	c. Basically the implemented classes of various Data Structures.



2. #### What are the types of Collections?

   Collections are of 3 types:

   ​	***a. System.Collections.Generic***

   ​	***b. System.Collections***

   ​	***c. System.Collections.Concurrent***



3. #### What is a Generic Collection?

   ​	a. It provides a generic implementation of standard data structures.

   ​	b. This collection is type safe, only 1 type of elements can be stored in this collection.

   ```c#
   // List
   List<int> list = new List<int>();
   
   // Queue
   Queue<int> queue = new Queue<int>();
   
   // SortedList
   SortedList<int, string> sortedList = new SortedList<int, string>();
   
   //Stack
   Stack<string> stack = new Stack<String>();
   
   // HashSet
   HashSet<int> set = new HashSet<int>();
   
   // LinkedList
   LinkedList<int> list = new LinkedList<int>();
   ```



4. #### What is Non-Generic Collection?

   ​	a. General purpose collection that can store elements of different types.

   ​	b. It is not type safe.

   ```c#
   // ArrayList
   ArrayList list = new ArrayList();
   
   // Hashtable
   Hashtable table = new Hashtable();
   
   // Queue
   Queue queue = new Queue();
   
   // Stack
   Stack stack = new Stack();
   
   // SortedList
   SortedList list = new SortedList();
   ```



5. #### What is a Concurrent Collection?

   ​	a. It provides thread-safe collection classes.

   ​	b. Used when multiple threads are accessing the collection simultaneously.

   ```c#
   1. BlockingCollection
   2. ConcurrentBag
   3. ConcureentDictionary
   4. Concurrent Queue
   5. ConcurrentStack
   6. ConcurrentPartitioner
   7. Partitioner
   ```





# 2. Collection Class



1. #### What is a Collection Class?

   ​	a. Collection<T> class provides the base class for a generic collection.

   ​	b. T is the type of elements in the collection.

   ​	c. Comes under ***System.Collections.ObjectModel***

   ​	d. Properties & Methods

   ```c#
   // Declaration
   Collection<string> coll = new Collection<string>();
   
   // Add()
   coll.Add("Hello");
   
   // Count
   coll.Count;	// 1
   
   // Clear()
   coll.Clear();
   
   // Contains()
   coll.Contains("Hello");	// true
   
   // Remove()
   coll.Remove("Hello");
   
   
   ```

   



# 3. Generics



1. #### What is Generic in C#?

   a. It's feature in C# that allows to define type-safe data structures.

   b. It's performance is better because of absence of boxing-unboxing & type-casting.



2. #### What is a Generic Class?

   It is a type-safe class that will work with any specified data type

   ```c#
   // Generic Class
   public class MyClass<T>{
   	private T data;
       public T value{
           get{
               return this.data;
           }
           set{
               this.data = value;
           }
       }
   }
   
   public class Program{
       static void Main(){
           MyClass<string> mc = new MyClass<string>();
           mc.value = "Hello";
           
           MyClass<int> mc2 = new MyClass<int>();
           mc2.value = 5;
           
           Console.Write(mc.value);	// Hello
           Console.Write(mc2.value);	// 5
       }
   }
   ```

   

3. #### What is a Generic Method?

   A type safe method that'll work with any provided data type

   ```c#
   public void Display<T>(string s, T value){
   	Console.Write(s + " " + value);
   }
   
   p.Display<int>("Integer", 34);
   p.Display<string>("String", "Hello");
   p.Display<double>("DOuble", 45.67);
   ```

   

4. #### What are the features of Generics?

   ​	a. It helps in code reuse.

   ​	b. It helps in performance due to absence of boxing-unboxing & typecasting.

   ​	c. It provides type safety, few errors in development.

   ​	d. We can create our own Generic classes, methods, interfaces and delegates.



5. #### What are the advantages of Generics?

   ​	***a. Reusability***

   ​		We can create a generic method that will return a sum if two numbers are provided, and will concatenate two strings if 		strings are provided.

   ​	***b. Type Safety***

   ​		This helps compiler to ensure that only selected type objects are to be passed into the collection.

   ​	***c. Performance***

   ​		Increased performance due to reduced boxing-unboxing & type-casting of variables.

   ```c#
   public void Add<T>(T a, T b){
       Console.Write(a+b);
   }
   
   Add<int>(2,3);	// 5
   Add<string>("Prajwal ", "Sharma");	// Prajwal Sharma
   ```

   



# 4. List Collection



1. #### What is a List Collection in C#?

   ​	a. It is a generic collection which stores data of ***same*** data type.

   ​	b. It is the generic version of ***ArrayList***.

   ​	c. It is of ***dynamic*** size

   ​	d. ***System.Collections.Generic*** namespace is used

   ​	e. Properties & Methods

   ```c#
   List<int> list = new List<int>();
   
   
   // Add()
   list.Add(1);	// add an element to list
   list.Add(2);
   list.Add(3);
   
   // Remove()
   list.Remove(1);	// Remove 1st occurance of element from list
   
   // RemoveAt()
   list.RemoveAt(0);	// Remove element at specified position
   
   // Clear()
   list.Clear();	// Empty the list
   
   // Sort();
   list.Sort();
   ```

   



# 5. SortedList



1. #### What is a SortedList in C#?

   ​	a. It is a list having Key-Value pairs sorted in ascending order based on keys.

   ​	b. It can be both generic & non-generic.
   
   ```c#
   SortedList list = new SortedList();
   // or
   SortedList list = new SortedList(){
       {1, "Hello"},
       {2, "World"}
   };
   
   list.Add(1,"This");
   list.Add(2, "is");
   list.Add(5, "list");
   list.Add(4, "sorted");
   list.Add(3, "a");
   
   foreach(DictionaryEntry pair in list){
       Console.Write(pair.Key);
       COnsole.Write(pair.Value);
   }
   
   //Methods
   1. Add(pair);
   2. Remove(key);
   3. RemoveAt(position);
   4. Clear();
   5. Contains(key);
   6. ContainsKey(key);
   7. ContainsValue(value);
   ```
   
   



# 6. HashSet



1. #### What is a HashSet?

   ​	a. A collection of unique elements.

   ​	b. It is generic

   ​	c. Uses sets & Hash table for storage.	

   ​	d. Duplicates are not allowed.

   ```c#
   // Method 1
   HashSet<int> set = new HashSet<int>();
   
   set.Add(1);
   set.Add(2);
   set.Add(3);
   
   // Method 2
   HashSet<int> set = new HashSet<int>(){1,2,3,4,5,6};
   
   // Methods
   
   1. Add(1);
   2. Remove(2);
   3. Clear();
   ```

   

2. #### What are Set Operations?

   ​	a. **UnionWith** (Set Union)

   ​	b. **IntersectWith** (Set Intersection)

   ​	c. **ExceptWith**

   ```c#
   HashSet<int> set = new HashSet<int>(){1,2,3,4,5,6,7,8};
   
   HashSet<int> set2 = new HashSet<int>(){4,5,6,7,8,9,10};
   
   // UnionWith - Combine 2 sets
   set.UnionWith(set2);	// 1,2,3,4,5,6,7,8,9,10
   
   // IntersectWith - Find common elements
   set.IntersectWith(set2);	// 4,5,6,7,8
   
   // ExceptWith - Remove common elements
   set.ExceptWith(set2);	// 1,2,3
   ```

   



# 7. SortedSet



1. #### What is a SortedSet?

   ​	a. It is a generic collection of elements sorted in ascending order.

   ​	b. Used when we need to store unique elements in a sorted order.

   ​	c. All HashSet methods are applicable.

   ```c#
   SortedSet<int> sortSet = new SortedSet<int>(){
     6,5,4,3,2,1  
   };
   
   foreach(var item in sortSet){
       Console.Write(i);	// 1,2,3,4,5,6
   }
   
   // Get maximum/minimum value
   sortSet.Max;	// 6
   sortSet.Min;	// 1
   
   // Methods
   1. Add();
   2. Clear();
   3. Contains();
   4. Reverse();
   ```

   

# 8. Dictionary



1. #### What is a Dictionary?

   ​	a. It is generic collection that stores key value pairs.

   ​	b. It is the generic version of Hashtable.

   ​	c. Keys are unique, compile time error will be thrown if you try to add same key.

   ```c#
   Dictionary<int, string> dict = new Dictionary<int,string>();
   
   dict.Add(1,"Hello");
   dict.Add(2,"World");
   
   foreach(KeyValuePair<int, string> pair in dict){
       Console.Write(pair.Key);
       Console.Write(pair.Value);
   }
   
   foreach(var i in dict.Keys){
       Console.Write(i);
       Console.Write(dict[i]);
   }
   
   // Methods
   1. Add(key,value);
   2. Remove(key);
   3. ContainsKey(key);
   4. ContainsValue(value);
   ```

   



# 9. SortedDictionary



1. #### What is SortedDictionary?

   a. A generic collection to store key value pairs in sorted order.

   b. It is similar to SortedList

   ```c#
   SortedDictionary<int, string> dict = new SortedDictionary<int, string>();
   
   dict.Add(1,"Hello");
   dict.Add(2, "World");
   
   
   foreach(KeyValuePair<int,string> pair in dict){
       Console.Write(pair.Key);
       Console.Write(pair.Value);
   }
   
   // Methods
   1. Add();
   2. Remove();
   3. Clear();
   4. ContainsKey();
   5. ContainsValue();
   ```

   



# 10. Hashtable



1. #### What is a Hashtable?

   a. It is a collection of Key-Value pairs arranged on the hash code of the key.

   b. It is non generic.

   c. It is the most optimal for lookups, O(1)

   d. Key is unique

   ```c#
   Hashtable ht = new Hashtable();
   
   ht.Add(1,"hello");
   ht.Add(2, "world");
   ht.Add("Prajwal", "Sharma");
   
   ht[1];	// hello
   ht[2];	// world
   ht["Prajwal"];	// Sharma
   
   
   foreach(var i in ht.Keys){
       Console.Write(i);
       Console.Write(ht[i]);
   }
   
   // Methods
   1. Add();
   2. Remove();
   3. Clear();
   4. ContainsKey();
   5. ContainsValue();
   ```

   



# 11. Stack



1. #### What is a Stack?

   a. It is a collection that implements Stack data structure.

   b. Elements are processed in LIFO order.

   c. It can be generic or non-generic.

   ```c#
   Stack<int> stack = new Stack<int>();
   
   stack.Push(1);	// Push 1 to stack
   stack.Push(2);	// Push 2 to stack
   stack.Push(3);	// Push 3 to stack
   
   stack.Pop();	// remove top element from satck
   stack.Pop();	// remove top element from stack
   
   stack.Peek();	// Get top element from stack
   
   stack.Clear();	// Clear the stack
   ```

   



# 12. Queue



1. #### What is Queue?

   a. It is a collection that implements Queue data structure.

   b. It process data in FIFO order.

   c. It can be generic or non-generic

   ```c#
   Queue<int> q = new Queue<int>();
   
   q.Enqueue(1);	// Add element to queue
   q.Enqueue(2);
   
   q.Dequeue();	// Remove first element from queue
   q.Dequeue();
   
   q.Peek();		// Get firt element from queue
   
   q.Count;		// Get size of queue
   
   q.Contains(2);	// Search for an element in queue
   ```

   

# 13. LinkedList



1. #### What is a LinkedList?

   a. It is a representation of LinkedList data structure.

   b. It is a generic class.

   ```c#
   LinkedList<string> list = new LinkedList<string>();
   
   list.AddLast("Hello");	// Hello
   list.AddLast("World");	// Hello -> World
   
   list.AddFirst("Yo");	// Yo -> Hello -> World
   
   list.AddAfter();		// Add after a given node
   list.AddBefore();		// Add before a given node
   
   list.First;				// Return 1st node
   
   list.Contains();		// Searches for a node in LL
   ```

   