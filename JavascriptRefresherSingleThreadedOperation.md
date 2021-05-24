# Javascript Refresher - Single Threaded Operation in All Cases


#Table of Contents
1. [Call Stack](#CallStack)
2. [Creation Phase](#CreationPhase)
3. [Execution Phase](#ExecutionPhase)
4. [Lexical Environment](#LexicalEnvironment)
5. [Asynchronous Callbacks](#AsynchronousCallbacks)
6. [Everything is an object](#Everythingisanobject)
7. [By Reference By Value](#ByReferenceByValue)
8. [this](#this)
9. [Spread Operator](#SpreadOperator)
10. [IIFE](#IIFE)
11. [Closures](#Closures)
12. [Factories](#Factories)
13. [Prototypical Inheritance](#PrototypicalInheritance)
14. [Var Let Const](#VarLetConst)
15. [Arrow Functions](#ArrowFunctions)
16. [Deconstructing](#Deconstructing)



## The Javascript Call Stack <a name="CallStack"></a> ##
![](https://cdn-images-1.medium.com/max/1600/1*-MMBHKy_ZxCrouecRqvsBg.png)

* The diagram above is to be studied and understood thoroughly

## Creation and Execution Phases

#### Creation Phase <a name="CreationPhase"></a>
* global object
* 'this'
* outer environment reference as global execution context
* memory space
* variables set to **undefined**
* functions declared

#### Execution Phase <a name="ExecutionPhase"></a>
* code executed **line by line**
* global execution context brings *this* and functions and outer link into play
* *scope* is where a variable is available 

#### Lexical Environment <a name="LexicalEnvironment"></a>
* where functions and variables are declared is not important; **where they are invoked is the key** 

![](https://miro.medium.com/max/902/1*Jr0HIJap0S2ILbNNTPhjBw.png)

* for **each function invocation/call a new execution context** is created
* as each function completes it is popped off the stack

#### Javascript's Solution to Blocking -- AsynchronousCallbacks <a name="Asynchronous Callbacks"></a>
* browser has features that operate outside the scope of the Javascript runtime engine

#### Javascript - Everything is an object ... <a name="Everythingisanobject"></a>
* except primitive types
* this includes unnamed functions assigned to variables as in the following code
```
var unnamedFunction = function()
  {
  console.log("Hello world")
  }
```
```
   unnamedFunction()
```

#### By Reference By Value <a name="ByReferenceByValue"></a>
* When a variable is assigned a primitive **value** and then another variable is set to equal (assigned) the first variable the second variable actually receives a *copy* of the primitive value not the original primitive value because the two variables are sitting in two different memory spaces in Javascript

* when a variable is set to an object then another variable is set equal (assigned) to the original variable the new variable gets a **reference** to the same location in memory as the first, no copy is made

#### 'this' <a name="this"></a>
* during the running of a function a new execution context is created which contains its variables and its outer environment and the this keyword.  Depending on how the function is called will determine what *this* refers to.  In the global context *this* refers to the global object; when *this* is called inside an object method it references the object that the method is sitting inside of.

#### Spread Operator <a name="SpreadOperator"></a>

```javascript
	const numbersArray = [2,4,6]
	console.log(sum(...numbersArray)) //12
```
	
#### IIFE <a name="IIFE"></a>
* immediately invoked functions run as soon as they are immediately invoked

```javascript
(function() {
  statements of code
  {)()
```

#### Closures <a name="Closures"></a>
* a closure is a section of code that allows an inner function to have access to the outer function's scope or lexical environment

```javascript
Function init() {
		  var name = 'Mozilla'

		  function displayName() {
		    alert(name)
		  }
		  
		  displayName()

		}

		init()
```
#### Factories <a name="Factories"></a>
* when a Javascript function creates an object it is referred to as a factory and functions much like in other object oriented languages

#### Prototypical Inheritance <a name="PrototypicalInheritance"></a>
* one object gets access to the properties and methods of another object

```javascript
function myFunction() {
  myFunction.prototype.whatever = “something”
  }
```

#### Var Let Const <a name="VarLetConst"></a>
* *var* keyword is scoped making it available outside the function
* *var* variables are available to be redeclared which sets up the possibility of accidentally redeclaring variables
* *let* keyword is block scoped meaning it is only available within the block it is created in
* *let* variables are not available to be redeclared
* *const*  variable is block scoped and does allow for the variable to be changed if the variable is an object; while a *const* object cannot be updated the properties within it can be

#### Arrow Functions <a name="ArrowFunctions"></a>
* standard functions
```javascript
function sum(a, b) {
	return a + b
}
```
can be rewritten as arrow functions
```javascript
let sum = (a, b) => a + b //everything after the arrow is assumed to be returned
```
* one parameter 
```javascript
function myPositive(number) {
	return number > 0
}
```
becomes
```javascript
let myPositive = number => number > 0
```
* no parameter
```javascript
function myRandomNumber () {
	return Math.random
}
```
becomes
```javascript
let myRandomNumber = () => Math.random
```
* passing a function as a parameter
```javascript
document.addEventListener('click', function() {
	console.log('Some event')
}
```
becomes
```javascript
document.addEventListener('click', () => console.log('Some event')
```

#### Deconstructing <a name="Deconstructing"></a>
* can be very useful in taking large objects and arrays and creating more manageable objects and arrays

* instead of using

```javascript
const alphabet = ['A', 'B', 'C', 'D', 'E', 'F', 'G', 'H']

const a = alphabet[0]
const b = alphabet[1]
```
the code can be re-written as

```javascript
const [a, , c, … leftover] = alphabet
```


<a href="#top">Back to TOC</a>







