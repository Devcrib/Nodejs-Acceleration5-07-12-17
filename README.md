<<<<<<< HEAD
# Nodejs-Acceleration5-07-12-17
Functional Programming
=======
### Functional Programming



Functional programming is a programming paradigm which is a way of thinking of software construction based on some defined principles. It is basically a style of writing programs by composing pure functions and also avoiding shared states, mutable data and side effects. It requires everything in building a software to wrapped in functions which includes writing lots of small reusable functions and simply calling them one after the other to get a result.

### Functional Programming in JavaScript

JavaScript has some important features needed for functional programming like First class functions, Annonymous functions and closures. However, JavaScript is a multi-paradigm  language which means it supports programming in many different styles, like procedural programming where functions represent a subroutine of instructions and can be reused anywhere in the program, object-oriented programming where objects are the main building blocks and as stated before, functional programming. Its support for other styles of programming tends to imply that everything needs to be mutable which goes against the principles of functional programming which are explained below.

## Principles of Functional Programming.

A brief summary of principles expected in functional programming include:

- No shared data which includes no access to global variables
- No mutable data
- No side effects
- No loops
- No variable declarations
- No void functions
- No object mutation

These principles are based on certain core-concepts of Functional Programming. These are:

 -   Pure Functions

 -   Shared State

 -   Side Effects

 -   Mutability/ Immutability

 -   Functors

 -   Higher-Order Functions

 -   Referential Transparency

 -   Function Composition

 -   Currying

     #### Pure Functions

     A pure function is a function which **always returns the same output when supplied with the same input at any point in time**. It also **does not have any side effects** which means it does not affect any other state outside itself. It can be said to be a stand-alone function which is not affected by any other function outside it and does not affect any other function outside itself. It must satisfy the conditions highlighted above for it to be considered a pure function.

     Let's consider the following code snippets to differentiate between pure and impure functions:

     ```function sqrt(){
     // function returns the square of an argument supplied
     //pure function because it returns the same value 
     //anytime it is called with same input
     function square(val){
       return val*val; 
     } 
     square(4); //returns 16 

     ```

     ```
     let exchangeRate = 325;

     function convert$ToNaira(amount){
       return exchangeRate * amount;
     } // impure function because it depends on an external variable.

     function writeName(name){
       console.log('Hello' +name);
     } //impure function becauses it causes a side effect by logging to the console.

     ```

     #### Shared State

     This involves any variable, object or memory space that exists in a shared scope or as the property of an object being passed between scopes. A shared scope can include global scope or closure scope. A shared state should be avoided in functional programming because in order to understand the effects of a function, you have to know the entire history of every shared variable that the function uses or affects.

     ```
     let exchangeRate = 325;
     //both functions share a global variable exchangeRate
     function convert$ToNaira(amount){
       return exchangeRate * amount;
     } // impure function because it depends on an external variable.

     function convert£ToDollar(amount){
       exchangeRate += 15; 
       return exchangeRate*amount;
     } 
     ```

     #### Side Effects

     A side effect effect is any application state change that is observable outside the called function other than its return value. This may include I/O(writing to the console, of logfile), modifying a mutable object, reassigning a variable, calling any other function with side effects etc.

     ```
     function writeName(name){
       console.log('Hello' +name);
     } //Causes a side effect by logging to the console.
     writeName('Ego') //Causes a side effect by logging 'Hello Ego' to the console.
     ```

     #### Mutation and Immutability

     Mutability means liable or subject to change or alteration. In programming, it means objects whose state is allowed to change over time. An immutable value is one whose value can never change after it has been created. In Javacript, strings and numbers are immutable by design. Declaring a variable with "const" would mean that there is no chance for it to be reassigned. However, the object can still be reassigned. To gain true immutability, the variable needs to be  assigned to an immutable data structure called trie data structures. which are effectively deep frozen, meaning that no property can change.

     Immutability pertains to all data structures, which includes arrays, maps, and sets. That means that we cannot call mutator methods such as `array.prototype.push` because that modifies the existing array. Instead of pushing an item onto the existing array, we can create a new array with all the same items as the original array, plus the one additional item.

     ​

     ### Functors

     A functor is something that can be mapped over. It's a container which has an interface that can be used to apply a function to the value inside it. They always supply mapping API. Take `map()` utility for example, it can act on a variety of data types by lifting the mapping operation to work with a functor API. The `Array.prototype.map()` has array as the container and allows you to abstract the data type from the mapping utility to make `map()` usable with any data type.

     #### High Order Functions

     It was stated above that JavaScript has first-class functions that can be passed around just like any other value, therefore, we can also pass a function to another function. We can also return a function from a function. This is called High Order Function. It is a function that takes a function as an argument and returns a function or both. Higher order function is usually used to Abstract or isolate actions, effects, async flow control of call-back function. To create utilities which can act on a wide variety of data types, take a list of functions and return some compositions of those input functions.

     ```
     const students = [
       {name : 'jeff', totalScore : 95 },
       {name : 'britney', totalScore : 90 },
       {name : 'deji', totalScore : 65 },
       {name : 'bassey', totalScore : 55 },
       {name : 'efe', totalScore : 70 },
     ];

     function calculateLowestScore(lowestScore,student){
       if( lowestScore > student.totalScore){
         return student.totalScore;
       }
       return lowestScore;
     }

     // To find the lowest score
     students.reduce(calculateLowestScore,student[0].totalScore); //  ==> 55

     ```

     ​

     #### Referential Transparency

     This was explained above as a very important quality of a pure function. It simply means that given a function and an input value, you will always receive the same output. That is to say there is no external state used in the function.The function always gives the same return value for the same arguments. The function cannot depend on any mutable state.

     #### Functional Composition

     this is the process of combining two or more functions in order to produce a new function or perform some computation. For example, the composition `f . g` (the dot means “composed with”) is equivalent to `f(g(x))` in JavaScript. There are two equivalent ways of thinking of it, as illustrated by this identity: `(f ∘ g)(x) = f(g(x))`. You can either think of `f ∘ g` as a single function or as the result of calling function `g`and then taking its output and passing that to `f`.

     It is important to note that we can compose any number of functions not necessarily just two and one way to compose functions is simply to take the output from one function and pass it to the next (i.e., `f(g(x))`). 

     ```
     function layFoundation(house){
       return {...house,foundation : 'laid'};
     }

     function layBricks(house){
       return {...house, bricks : 'laid'};
     }

     function constructRoof(house){
       return {...house , roof : 'built'};
     }

     //To built our house {}
     //We call out functions like 

     constructRoof(layBricks(layFoundation({}))) ==> {foundation: "laid", bricks: "laid", roof: "built"}
     ```

     ​

     #### Declarative and Imperative Programming

     Functional programming is a declarative paradigm. This means that the logic of computation is expressed without explicitly describing the flow of control. It declares what is to be done not stating how it should be done.

     **Imperative** programs have lines of code which describe the steps used to achieve the desired results.

     **Declarative** programs abstract the flow control process, and instead spend lines of code describing the data flow. The how gets abstracted away.

     For example, a function which takes an array of number and returns the array with each number divided by 2.

     ```
     //imperative programming describes each step to achieve the result
     const divide = nums => {
       const newValues = [];
       for (let i = 0; i < nums.length; i++) {
         newValues.push(nums[i] / 2);
       }
       return newValues;
     };

     console.log(divide([8, 10, 16])); // would return [4, 5, 8]
     ```

     ```
     //declarative programming hide how it should be done
     const divide = nums => nums.map(n => n / 2);

     console.log(divide([8, 10, 16])); // [4, 5, 8]
     ```

     #### Lambdas and Closures

     Lambda means function used as data. The function is passed as  an argument to another function, returned as a value from a function, or  assigned to variables or data structures. 

     Closures are a mechanism for containing state. In JavaScript, a closure is created whenever a function accesses a variable defined outside the immediate function scope. Closure is created simply by defining a function inside another function, and exposing the inner function, either by returning it, or passing it into another function. The variables used by the inner function will be available to it, even after the outer function has finished running. Closures are a way of hiding your data and making them private.

     #### Recursion

     Recursion is an important programming technique, in which a function calls itself. The example below calculates the factorial of a number iteratively and recursively.

     ```
     function factorial(n){  
         // If the number is less than 0, return -1.  
         if (n<0) {  
             return -1;  
         }  
         // If the number is 0, its factorial is 1.  
         else if (n === 0) {  
             return 1;  
         }  
         let temp = n;  
         while (n >= 2) {  
             temp *= n;  
         }  
         return temp;  
     }  

     console.log(factorial(8)); // givees 40320  
     ```

     ```
     function factorial(n){
       //Base case ---stop the recursion
       if(n===0){
         return 1; //0! is defined to be 1
       }
       return n* factorial(n-1);
     }
     console.log(factorial(8)); //gives 40320
     ```

     All these concepts allow us to create applications that have functionalities that don't depend on the state of one another, this allows for easy debugging and true  separation of concerns as change in any function does cause a side effect in other parts of the application.

     However, It should be noted that even though functional programming seems like the holy grail of programming, it is impossible to create applications with 100% pure functions. The 80 / 20 is adopted in this case where 80% of the app are pure and 20% impure and this is where "impure" operations like API calls, logging, managing state are done.

     Happy functional programming!!!!.

     References

- https://medium.com/javascript-scene/master-the-javascript-interview-what-is-functional-programming-7f218c68b3a0
- https://opensource.com/article/17/6/functional-javascript
>>>>>>> made by node members
