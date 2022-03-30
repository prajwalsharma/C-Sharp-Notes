## 1.Execution Context

1. Everything in JS happens inside the **Execution Context**.
2. It has two components:
   1. **Memory** (Variable Environment)
      1. Variables are stored here as key-value pairs.
      2. Functions are stored here as key-value pairs.
   2. **Code **(Thread of Execution)
      1. Code is executed here one line at a time in this thread.



## 2. Synchronous Single Threaded

1. JS is a synchronous single-threaded language.
2. JS can execute only one command at a time in a specific order.



## 3. What happens when you run JS code?

1. First Execution Context is created in 2 phases:

   1. **Memory Creation** phase

      1. JS allocate memory to variable '**n**', '**square**', '**square2**', '**square4**' and store key-value pair in Memory

         ```javascript
         n: undefined
         square: { Whole function code }
         square2 : undefined
         square4 : undefined
         ```

   2. **Code Execution** phase

      1. JS again read the whole code line by line.
      2. Value of '**n**' will be stored in Memory as '2'.
      3. JS will skip the function '**square**' because there is nothing to execute.
      4. When JS reach function invocation code:
         1. JS create a new **Execution Context** within the **Global Execution Context** and store it in **Code Execution**.
         2. JS will create a Memory Creation phase.
            1. JS will allocate memory to '**num**' & '**ans**' in memory and assign 'undefined'.
         3. JS will create a Code Execution phase.
            1. JS will execute each line of code one by one.
            2. JS will fetch the value of '**n**' from memory & assign it to variable '**num**' as 2.
            3. JS will calculate (**num** * **num**) and assign the value of '**ans**' as 4 in memory.
            4. JS will see the '**return**' keyword and return the control to parent Execution Context.
            5. JS will now assign the value returned to the variable '**square2**' as 4.
            6. The whole Child Execution Context will be deleted.
            7. Same thing happen for '**square4'** function invocation.
            8. Once the program is completed, whole Execution Context will be destroyed.

```javascript
var n = 2;

function square(num){
    var ans = num * num;
    return ans;
}

var square2 = square(n);

var square4 = square(4);
```



## 4. How JS manage the Execution Context?

1. JS uses "**Call Stack**" to manage Execution Contexts.
2. It's a stack that stores the Global Execution Context and all child Execution Contexts in LIFO order.
3. During function invocation, a newly created EC is pushed into '**Call Stack**'.
4. Once the function call is completed, the EC is popped from '**Call Stack**'.



## 5. Hoisting

1. Hoisting is a phenomenon in JS through which we can access variables & functions even before initializing them without any error.

2. Hoisting uses the concept of Execution Context.

3. Initially the variables are created in memory with value undefined.

4. Function is stored in the memory so function is working fine.

   ```javascript
   getName();
   console.log(x);
   
   var x = 7;
   
   function getName(){
       console.log("Hello Prajwal!");
   }
   
   // Hello Prajwal!
   // undefined
   ```

   ```javascript
   getName();
   console.log(x);
   
   //var x = 7;
   
   function getName(){
       console.log("Hello Prajwal!");
   }
   
   // Hello Prajwal!
   // Error - x is not defined
   ```



## 6. How functions work in JS

1. Total 2 child Execution Context will be created.
2. In first child EC, the variable x will be created and destroyed after.
3. In second child EC, the variable x will be created and destroyed after.
4. In the end, in Global EC x will remain with value 1.

```javascript
var x = 1;

a();
b();

console.log(x);

function a(){
    var x = 10;
    console.log(x);
}

function b(){
    var x = 100;
    console.log(x);
}

// 10
// 100
// 1
```



## 7. What happens when you build the JS code?

1. A Global Execution Context is created by JS engine.

2. A '**window**' global object is created by JS engine.

3. A '**this**' object is also created by JS engine that points to '**window**' object.

4. Any variable written outside of any function is stored in '**Global Space**'.

5. Such variables will automatically added to the '**window**' object.

   ```javascript
   var a = 10;
   
   function b(){
       var x = 10;
   }
   
   console.log(windows.a);	// 10
   console.log(a);	// 10;
   console.log(x);	// undefined
   console.log(this.a)	// 10
   ```



## 8. Undefined vs Not Defined

1. When Execution Context is created, JS engine assigns default value '**undefined**' to all the variables in Memory.

   ```javascript
   console.log(a);
   var a = 7;
   console.log(a);
   console.log(x);
   
   // Undefined
   // 7
   // Error: Not Defined
   ```



## 9. JavaScript is loosely/weak typed language?

1. A variable can be assigned int, string or decimal so there is no strict type checking, that is why it's loosely coupled.



## 10. The Scope Chain & Lexical Environment

1. A child Execution Context can access variable created in parent Execution Context.
2. A parent Execution Context cannot access variables created in child Execution Context. 
3. The '**c**' function is lexically sitting inside '**a**' function. 
4. The 'a' function is lexically sitting inside Global EC.
5. A **Lexical Environment** is created in Memory phase that contains local memory + the reference to it's parent's Lexical Environment.
6. Lexical Environment for Global EC is null.
7. The whole chain of Lexical Environments is called **Scope Chain**.
8. The function 'c' is enclosed inside function 'a' and has access to it's parent's scope and that is called '**closure**'.

```javascript
function a(){
    
    var c = 100;
    
    console.log(b);	// 10
    
    c();
    
    function c(){
        console.log(b);	// 10
    }
    
}

var b = 10;

a();

console.log(b);	// Not Defined
```



## 11. Let & Const & Temporal Dead Zone

1. Let & Const are also '**Hoisted**' and memory is allocated.
2. But the memory is allocated not in ''**Global**'' memory space, but in ''**Script**'' memory space where we cannot access without initializing.
3. **Temporal Dead Zone** is the time between let/const variable hoisted & till assigned a variable.
4. Variable '**a**' will be in **Temporal Dead Zone** until it's value is not assigned from undefined in "**Script**" memory space.
5. **ReferenceError** is thrown when we're trying to access variables in **Temporal Dead Zone**.

```javascript
console.log(a); // ReferenceError - Hoisted but not accessible - value is 'undefined'
console.log(b);	// undefined (Hoisting)

let a = 10;
var b = 100;

window.b;	// 100
this.b;		// 100

window.a;	// undefined - because it's not stored in Global space.
this.a;		// undefined - because it's not stored in Global space.

var b = 100000;		// Correct
let a = 100000;		// SyntaxError

const c;		// SyntaxError
const c = 10;	// Correct
c = 20;			// TypeError
```



## 12. ReferenceError vs SyntaxError vs TypeError

1. **TypeError** - Reassigning a value to constant type.
2. **SyntaxError** - Wrong syntax is written.
3. **ReferenceError** - If variable is not created or variable is in Temporal Dead Zone.



## 13. Recommendation

1. Use "**const**" first.
2. Use "**let**" second because it will throw error straight away.
3. Never use "**var**" because it can be undefined and will never throw error.
4. Put all variable declarations & initialization at the top in JS. We can decrease the time of TDZ to 0 by doing this.



## 14. Block Scope

1. A "**Block**" is a piece of code grouped in curly braces.

2. All code in a function/if/loop is a block.

3. All let/const variables in curly braces are stored in a special memory called "**Block Scope**".

4. All variables & functions inside Block scope cannot be accessed from outside the block.

   ```javascript
   {
       var a = 10;
       let b = 20;
       const c = 30;
       
       console.log(a);	// 10
       console.log(b);	// 20
       console.log(c);	// 30
   }
   
   console.log(a);	// 10 - Stored in Global Scope
   console.log(b);	// ReferenceError - Stored in Block scope
   console.log(c);	// ReferenceError - Stored in Block scope
   ```



## 15. Shadowing

1. **Shadowing** is a process where a variable in Block scope shadows the variable with same name outside the block.

2. Both variables 'a' are storing same reference in Global Space.

   ```javascript
   // Global Scope
   var a = 10;
   {
       var a = 20;
       console.log(a);	// 20
   }
   console.log(a);	// 20 - Shadowing
   
   
   // Global Scope & Block Scope
   let b = 10;
   {
       let b = 20;
       console.log(b);	// 20 - Stored in Block Scope
   }
   console.log(b);	// 10 - Stored in Script Scope
   ```



## 16. Closures

1. Function along with it's Lexical Scope together is called **Closure**.
2. This closure has access to it's parent's Lexical Scope.
3. When we called function "x" and stored the result function "y" in "z", the whole function "x" is destroyed.
4. Now when we call the function "z", it will still print 7 because it remembers it's Lexical Scope at that time. The value 7 was present in it's Lexical Scope so it printed 7.
5. When we return a function, it returns a **Closure**. The functions remembers it's data.
6. Closures are used in Currying, Memoize, setTimeouts, Iterators etc.

```javascript
function x(){
    
    var a = 7;
    
    function y(){
        console.log(a);
    }
    
    return y;
}

var z = x();

z();	// 7 - This is Closure
```





## 17. Closure & setTimeout

```javascript
function x(){
    var i = 1;
    setTimeout(() => console.log(i), 3000);
    console.log("Hello");
}

x();

// Hello
// 1 - after 3 seconds
```

```javascript
function x(){
    
    for(var i=1; i<=5; i++){
        
        setTimeout(() => console.log(i), i * 1000);
        
    }
    
}

x();

// 6
// 6
// 6
// 6
// 6

// Due to closures, each function has reference of variable i in it's lexical scope, after the loop ends, the value of i will be 6. Therefore 6 is printing.

// To solve this, we can use let, instead of var because due to let each i will have different value stored in block scope.

// Or we can use closures so that we can have different copy of i

function x(){
    for(var i=1; i<=5; i++){
        function y(int z){
            setTimeout(() => console.log(z), z * 1000);
        }
        y(i);
    }
}
x();	// Correct

// Now each method call, a new value if input parameter will be stored.
```





## 18. Function Jargons for Interviews

```javascript
// 1. Function Statement / Declaration
function a(){ console.log("This is function statement") }
    

// 2. Function Expression
var b = function (){ console.log("This is function expression") };


// 3. Difference b/w Function statement & expression is "HOISTING". "a" will store function code while "b" will contain undefined in Memory.


// 4. Anonymous Function
var c = function(){};	// A function without a name


// 5. Named Function Expression
var c = function d(){};	 // A function with a name
d();	// ReferenceError - Because memory is not created for this function yet.


// 6. Parameters vs Arguments
function a(var x, var y, var x){};	// Parameters
a(1,2,3);	// Arguments


// 7. First Class Functions/Citizens
// Ability to pass function to another function or a function returning another function is called First Class Function


// 8. Arrow Functions
var a = () => {console.log("This is an anonymous function")};
```





## 19. Callback Functions

1. A function passed as an argument to another function is called **Callback Function**.
2. We can do async things in JS using Callback functions.
3. **setTimeout(fn, 5000)** is passed a callback function that will be executed after some time.
4. setTimeout will not guarantee to be executed after 5 seconds.





## 20. Event Listeners

```javascript
document
    .getElementById("clickMe")
    .addEventListener("click", () => console.log("Callback function"));

// This function will be stored in Browser's DOM API and will put into JS call stack when btn is clicked
```





## 21. Closures with Event Listener

```javascript
function attachEventListeners(){
    let count = 0;
    document
        .getElementById("clickMe")
        .addEventListener("click", () => console.log("Button Clicked",++count));
}

attachEventListeners();

// The callback function has access to variable "count", and everytime button is clicked the value will be incremented and due to closure the callback function have the reference to "count" and it's value.
```





## 22. Garbage Collection & removeEventListener

1. **eventListeners** are very heavy in memory & due to closures it will hold the references to all the local variables.
2. If we have thousands of such eventListeners on our page, our memory usage will increase.
3. When we use **removeEventListener**, all such variables will be garbage collected and memory will be released.





## 23. Asynchronous JS & Event Loop

1. JS has only 1 call stack and can do one task at a time.

2. If we want to call a function after some time, we need a superpower (Timer).

3. This superpower will be provided by the browser.

4. Browser contains many superpowers (Web APIs) including **Timer**, **LocalStorage** **Database**, **Fetch API**, **DOM** APIs, **Bluetooth**, **Location** etc.

5. These APIs are not part of JS but are part of browser and stored in "**window**" object.

6. After 5 seconds, Timer API will push the callback method into "**Callback Queue**".

7. Once everything is executed in "**Call Stack**", "**Event Loop**" will pop the callback method and push it into "Call Stack".

8. **Event Loop** is used to continuously monitor "Call Stack" & "Callback Queue" & moves the call-backs from queue to stack.

9. We need "**Callback Queue**" to maintain FIFO order of all incoming events.

10. We have "**Micro Task Queue**" that is used to store call-backs related to **Promises** & **Mutation Observers**.

11. "**Event Loop**" will give priority to "**Micro Task Queue**" and empty is first then the "**Callback Queue**" will be emptied.

12. "**Starvation**" happens when a callback function calls another callback function and so on.

    ```
    Browser APIs
    
    1. setTimeout() - Timer superpower
    2. getElementById() - DOM API superpower
    3. fetch() - Fetch API superpower
    4. localStorage - Storage API superpower
    5. console.log() - Console API superpower
    6. location - GeoLocation API superpower
    ```

    ```javascript
    // Example 1
    
    console.log("Start"); // Call the console API that will print on console
    
    setTimeout(() => console.log("Callback"), 5000); // Pass the function to Timer API
    
    console.log("End"); // Call the console API that will print on console
    
    // Now the Timer API will push the callback function into "Callback Queue" & then "Event Loop" will take this callback function and push into "Call stack".
    ```

    ```javascript
    // Example 2
    
    console.log("Start");
    
    document
        .getElementById("btn")
    	.addEventListener("click", () => console.log("Callback"));	// Pass the CB fun to the DOM API
    
    console.log("End");
    
    // When the button is clicked, DOM API will push the callback into "Callback Queue" from where "Event Loop" will pick it up & push into "Call Stack" and it will be executed.
    ```

    ```javascript
    // Example 3
    
    console.log("Start");
    
    setTimeout(() => console.log("Callback Timer"), 5000);
    
    fetch("URL").then(() => console.log("Callback Network"));
    
    console.log("End");
    
    // "Callback Timer" will be stored in Timer API
    // "Callback Network" will be stored in Fetch API
    
    // "Callback Timer" will be pushed into "Callback Queue" after 5 seconds
    // "Callback Network" will be pushed into "Micro Task Queue", another Queue browser maintain.
    ```





## 24. setTimeout() delay

1. setTimeout() does not guarantee the delay because "**Event Loop**" will first empty the "Call Stack" & then the "**Micro Task Queue**".
2. So if we have long running tasks in "**Call Stack**" then "**Event Loop**" will wait until all long running tasks are completed.
3. Now the setTimeout callback will be pushed into "**Call Stack**".
4. This whole delay may take some extra time.
5. setTimeout(function, 0) will execute in the same way.





## 25. Higher Order Function

1. A function that takes another function as an argument or returns another function is called **HOF**.
2. **map**, **filter** & **reduce** functions are **Higher Order Functions**.





## 26. map, filter & reduce

1. **map**

   ```javascript
   // Map will transform each and every value of the array and return a new array
   
   var a = [1,2,3,4,5];
   
   function b(c){
       return c * 2;
   }
   
   var d = a.map(b);
   
   console.log(d);	//	[2,3,6,8,10]
   ```

   

2. **filter**

   ```javascript
   // Filter will filter the array
   
   const arr = [1,2,3,4,5];
   
   function isEven(int x){
       return x%2 == 0;
   }
   
   const c = arr.filter(isEven);
   
   console.log(c);	// [2,4]
   ```

   

3. **reduce**

   ```javascript
   // Reduce will take all elements of the array, do something with them, and return a single value.
   
   const arr = [1,2,3,4,5];
   
   function reduceExample(accumulator, current){
       accumulator += current;
       return accumulator;
   }
   
   const c = arr.reduce(reduceExample, 0);
   
   console.log(c);	// 15
   ```

   ```javascript
   // Find fullname of all users
   
   const users = [
     {firstName : "Akshay", lastName: "Saini", age : 26},
     {firstName : "Doland", lastName: "Trump", age : 75},
     {firstName : "Elon", lastName: "Musk", age : 50},
     {firstName : "Deepika", lastName: "Padukone", age : 32},
   ];
   
   function getFullName(a){
     return a.firstName + " " + a.lastName;
   }
   
   const newarr = users.map(getFullName);
   
   console.log(newarr);
   ```

   ```javascript
   // Find all different ages and count of users against each user
   
   const users = [
     {firstName : "Akshay", lastName: "Saini", age : 26},
     {firstName : "Doland", lastName: "Trump", age : 75},
     {firstName : "Elon", lastName: "Musk", age : 75},
     {firstName : "Deepika", lastName: "Padukone", age : 32},
   ];
   
   function ageGroup(result, current){
     if(result[current.age]){
       result[current.age] += 1;
     }
     else{
       result[current.age] = 1;
     }
     return result;
   }
   
   var result = users.reduce(ageGroup,{});
   
   console.log(result);
   ```

   ```javascript
   // Get first name of all users having age less than 30
   
   const users = [
       {firstName : "Akshay", lastName: "Saini", age : 26},
       {firstName : "Doland", lastName: "Trump", age : 75},
       {firstName : "Elon", lastName: "Musk", age : 75},
       {firstName : "Deepika", lastName: "Padukone", age : 26}
   ];
   
   const usersWithAgeLessThan30 = (user) => user.age < 30;
   
   const getFirstName = (user) => user.firstName;
   
   const result = users.filter(usersWithAgeLessThan30).map(getFirstName); // Method Chaining
   
   console.log(result);
   ```





## 27. Polyfills

Map, Reduce & Filter are part of ES-6 which is not available for all browsers. **Polyfills** are the actual code written in these methods.

1. **map**

   ```javascript
   // Map is a function that take another function as input
   
   let arr = [1, 2, 3, 4, 5];
   
   const square = x => x * x;
   
   const myPolyfill = (myArray, myFunction) => {
   
     let result = [];
   
     // Execute the callback function for each array element
     for (let i of myArray) {
       result.push(square(i));
     }
   
     return result;
   };
   
   let result = myPolyfill(arr, square);
   
   console.log(result);
   
   ```

   

2. **filter**

   ```javascript
   // Filter will take only those elements, for which the callback function will return true
   
   let arr = [1, 2, 3, 4, 5];
   
   const isEven = (x) => (x % 2 == 0);
   
   const filterPolyfill = (myArray, myCallbackFunction) => {
   	
     let result = [];
     
     for(let i of myArray){
     	if(myCallbackFunction(i)){
       	result.push(i);
       }
     }
     
     return result;
     
   }
   
   const result = filterPolyfill(arr, isEven);
   
   console.log(result);
   ```

   

3. **reduce**

   ```javascript
   // Reduce will execute a callback function and merge the results
   
   let arr = [1, 2, 3, 4, 5];
   
   const sum = (sum, current) => {
       sum += current;
       return sum;
   }
   
   const reducePolyfill = (myArray, myFun, defaultValue) => {
   
       let result = defaultValue;
   
       for(let i of myArray){
           result = myFun(result, i);
       }
   
       return result;
   
   }
   
   const result = reducePolyfill(arr, sum, 0);
   
   console.log(result);
   ```

   
