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

















































































