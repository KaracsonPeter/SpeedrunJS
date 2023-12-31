# Let's learn JS as fast as possible!

## Variables
Variables are containers in which you can store anything you want ... like:
 - Base variables: 
   - Integers numbers
   - Floating point numbers
   - Characters
 - Complex variables:
   - String
   - Some kind of object

You can refer to the content of your container by its name.

```js
// Global scope
let simpleVariable = 'Hello';
let anotherVariable = "world!";

// MESSAGE is "Hello world!" now!
const MESSAGE = simpleVariable + anotherVariable;

let GLOBAL_VARIABLE = 20;
const PI = 3.1415;

// Local scope
{
    let simpleVariable = 2;
    // Here simpleVariable is 2
}
// Here simpleVariable is 'Hello'

// Assign another type
simpleVariable = 2;

// Exponential Notation
let y = 123e5;    // 12300000
let z = 123e-5;   // 0.00123 

// BigInt (long integers)
BigInt(617832459823491257);

// Different representations of byte contents
// Hexadecimal
let hex = 0x019ABCDEFn;
// Octal
let oct = 0o701234567n;
// Binary
let bin = 0b10101010n;
```

## Data types
Javascript numbers are always one type: double (64-bit floating point).  
IEEE 754:
- number (the fraction) is stored in bits 0 to 51
- exponent in bits 52 to 62
- sign in bit 63

### Number
```js
let a = 1.1
```
#### Members methods
Returns a number:
```js
toString()	    // as a string
toExponential() // written in exponential notation
toFixed()       // written with a number of decimals
toPrecision()   // written with a specified length
ValueOf()       // as a number
```

#### Properties
```js
EPSILON           // The difference between 1 and the smallest number > 1.
MAX_VALUE         // The largest number possible in JavaScript
MIN_VALUE         // The smallest number possible in JavaScript
MAX_SAFE_INTEGER  // The maximum safe integer (253 - 1)
MIN_SAFE_INTEGER  // The minimum safe integer -(253 - 1)
POSITIVE_INFINITY // Infinity (returned on overflow)
NEGATIVE_INFINITY // Negative infinity (returned on overflow)
NaN               // A "Not-a-Number" value
```

### Booleans
```js
let x = true;
```

### Object (Detailed explanation later.)
```js
const human = {name:"Joe", color:"white"};
```

### None or Infinity type
```js
let x = NaN;
let y = Infinity;
```

### Array 
This is a special standard JS class. (Detailed explanation later.)
```js
const nums_1 = [1,2,3];
let nums_2 = [4,5,6];
```
Difference between const and let is only that the reference to which the defined name points can (let) or cannot (const) be changed.
```js
num_2 = num_1; // Works, num_2 will be [1,2,3]
// num_1 = num_2; // ERROR
```
Overwrite a value at an index:
```js
nums_1[0] = 5; // This will work since we did not change the reference, only the value behind it
```
#### Properties of array objects
```js
const testArray = [1, 2, 3]
testArray.length // - number of elements in the array
testArray.prototype.newCustomElement  // - allows you to specify custom properties to your array object
testArray.constructor
testArray.input
testArray.index
```

#### Functions of array objects
toString() - convert array content to string
```js
const testArray = [1, 2, 3];
testArray.toString(); // String: "1,2,3"
```
forEach() - iterate through array elements
```js
// Every function is a Callback function if it is called by code parts other than you wrote.
const testArray = [1, 2, 3]
let sum = 0;
testArray.forEach(callbackFunction);
function callbackFunction(testNumber) {
  sum += testNumber;
}
```
push() - append element at the end of the array
```js
const testArray = [1, 2, 3];
let testArrayLength = testArray.push(4); // now testArray = [1, 2, 3, 4]
```
pop() - take out the last element to your variable
```js
const testArray = [1, 2, 3];
let lastElement = testArray.pop(); // now testArray = [1, 2], lastElement = 3
```
every() - Returns all elements meets the criteria of callback function
some() - Returns true if any of the array elements meets callback criteria
```js
const testArray = [1, 2, 3];
let allLargerThanZero = testArray.every(conditionFunction); // true
function conditionFunction(passedNumber, index, array) {
  return passedNumber > 0;
}
// Same logic for "some()"
```
concat() - Concatenate 2 array together:
```js
const testArray_1 = [1, 2];
const testArray_2 = [3, 4];
const result = testArray_1.concat(testArray_2); // result is [1, 2, 3, 4]
```
join() - Creates a string from the array, where elements are separated by a specific user defined string
```js
const testArray = [1, 2, 3];
let csvStr = testArray.join('; '); // csvStr = "1; 2; 3"
```  

flat() - Flatten an array of arrays to a single array
```js
const testArray = [[[1, 2],[3, 4]],[5]];
const flattenedArray = testArray.flat(); // flattenedArray = [1, 2, 3, 4, 5]
```  

splice() - Insert multiple elements into an array with optional overwrite N of them.  
```js
const letters = ['a', 'z', 'e'];
const index = 1;
const overwrite = 1;
letters.splice(index, overwrite, 'b', 'c', 'd'); // letters = [a,b,c,d,e]
```

slice() -   
```js
const nums = [-2, -1, 0, 1, 2];
const zPlus = nums.slice(2); // zPlus = [0, 1, 2]
```

##### See a [documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) for other functions:  
shift(), unshift() - Same as push and pop but operates at the front of the array  
indexOf() - Returns the first index of the searched element  
lastIndexOf() - Returns the last index of the searched element  
filter() - Subset shall returned from the original array. These subset elements meets the criteria of a callback function.  
map() - Creates a new array by performing a function on each array element  
from() - Returns an array object from any object defining property "length"  
includes() - Returns if an element is within an array or not  
delete() - Creates an undefined hole on your array, wherever you want  

### String
String is a special standard JS class. We will talk about classes later. You can skip this chapter and after classes, you will have a better understanding of this.  

#### Define strings
```js
// Fine
let name_0 = "John";
let name_1 = "John";
name_0 == name_1; // true
name_0 === name_1; // also true

// Also fine:
let name_2 = new String("Mary");
BUT!
let name_3 = new String("Mary");
name_2 == name_3; // this is false
name_2 === name_3; // also false
```

#### Template Strings / Literals
Instead of adding strings and variables together, the best-practice is to use Template Literals.
```js
let x = 2;
let y = "four";
`${x} * ${x} = ${y}`;  // "2 * 2 = four"
`<h2>${x} * ${x} = ${y}</h2>` // Header2: "2 * 2 = four"
```

#### String member (property) variables
See documentation:
```js
length
```

#### String member (property) functions
See documentation:
```js
slice()
substring()
substr()
replace()
replaceAll()
toUpperCase()
toLowerCase()
concat()
trim()
trimStart()
trimEnd()
padStart()
padEnd()
charAt()
charCodeAt()
split()
indexOf()
lastIndexOf()
search()
match()
matchAll()
includes()
startsWith()
endsWith()
```

### Date object (detailed explanation later on)
```js
const date = new Date("2022-03-25");
```


## Operators
### Arithmetic Operators
```js
// Define variables to play around with
let x = 3;
let y = 4;
z = x + y; // 'z' is 7 now  (Addition)
y - x; // 1                 (Subtraction)
x * y; // 12                (Multiplication)
x / y; // 0.75              (Division)
x**3;  // 27                (Exponentiation)
y % x; // 1                 (Modulus)    (4/3 = 1 -> remainder = 1)
x++;   // x = 4 now!        (Incrementing)
x--;   // x is 3 again!     (Decrementing)
```

### Assignment Operators
```js
x = y 	-> equivalent to ->    x = y
x += y 	-> equivalent to ->    x = x + y
x -= y 	-> equivalent to ->    x = x - y
x *= y 	-> equivalent to ->    x = x * y
x /= y 	-> equivalent to ->    x = x / y
x %= y 	-> equivalent to ->    x = x % y
x **= y -> equivalent to ->    x = x ** y
```

### Comparison Operators
```js
// "Simple" equal to
2 == '2' // true
2 == 3   // false

// equal value AND equal type
2 === '2' // false
2 === 2   // true

// not equal
2 != '2' // false
2 != 3   // true

// not equal value OR not equal type
2 !== '2' // true
2 !== 2   // false
2 !== 3   // true

// greater than
3 > 2 // true
2 > 2 // false
1 > 2 // false

// less than
3 < 2 // false
2 < 2 // false
1 < 2 // true

// greater than OR equal to
3 >= 2 // true
2 >= 2 // true
1 >= 2 // false

// less than or equal to
3 <= 2 // false
2 <= 2 // true
1 <= 2 // true

// ternary operator
let a = condition ? 10 : 20; // if 'condition' is 'true', than a is '10', otherwise it is '20'
a = true ? 10 : 20  // 10
a = false ? 10 : 20 // 20
```

### String Operators
```js
'A' > 'B'; // false
'A' < 'B'; // true
'B' < 'A'; // false
'B' > 'A'; // true
'a' > 'B'; // true (because it works based on ASCII code)
'20' > '5';// false (because these are strings)
'20' > 5;  // true (because it is interpreted as integer comparison)
let a = "Hello" + 'darkness'
a += "my old friend!" // a = Hello darkness my old friend!
"5" + 5;   // 55
```

```js
OK
```
```js
'20' + 5; // 205
'20' - 5; // 15
'20' > 5; // true
"2" + "2" - "2" // 20
```

```js
('b' + 'a' + + 'a' + 'a').toLowerCase(); // banana
```

### Logical Operators
```js
true && true;   // true
true && false;  // false
false && false; // false

true || true;   // true
true || false;  // true
false || false; // false

true && !true;  // false
!true || false; // false
false || !false;// true
```

### Bitwise Operators
```js
6 & 2; // 2 (because 0110 & 0010 = 0010 = 2)
6 & 1; // 0 (because 0110 & 0001 = 0000 = 2)
0b00001111 & 0b01010101; // 5 (0b00000101)
0b00000001 << 8; // 256
```

```js
<!DOCTYPE html>
<html>
<body>

<p id="0"></p>
<p id="1"></p>
<p id="2"></p>
<p id="3"></p>

<script>

let a = 0b00000001;
for (let i = 0; i < 4; i++) {
  document.getElementById(i.toString()).innerHTML = a <<= 1; // 2, 4, 8, 16
}
</script>

</html>
```

```js
~5; // NOT
^5; // XOR
>>> // unsigned right shift
```
## Functions
Functions or methods are special type of variables. The difference is that they do not define a number. Instead of that they define a code fragment within the scope of the function. This code can be `called` multiple times as we will see.  
Previously, we have discussed that scope is defined by curly bracket: `{}`. This is also true for `function` definitions.  
In JS, you can define a function with the help of keyword `function`:
```js
function addition(local_a, local_b) {
	let local_result = local_a + local_b;
    return local_result;
}
```
The name of this function definition above is `addition`. After this name, you must place round brackets. Inside that, you can specify so-called `parameter`s of the function, if you want to. These are the inputs of the function. These variables belong to the scope of the function and must be specified by the caller!  
Keyword `return` signs what should be given back as the result (or output) of the function call. This output is passed to the caller.  
You don't need to specify these always. You can have as many inputs or parameters as you want, and you can have or cannot have an output or return value. The following definition has no parameters and return at all:
```js
function this_function_has_no_parameters_and_return_value() {
  // log something into the console
  console.log("Hello world!");
}
```
You can `call` your defined code part (function), by writing it's name and parameters like this:a
```js
let global_result = addition(2, 3);  // global_result shall be 5
```
Note: when you call your function, you must specify the exact same amount of parameters in the correct order!  

Just to see that functions are variables as-well:
```js
let redefined_addition = addition;
let global_result_2 = redefined_addition(2, 3); // global_result_2 is also 5
```
### Lambda
Lambda functions are "brief" functions which have no name but specifies a code part just like a normal function definition.
You can assign these un-named functions to variables:
```js
const addition_2 = (a, b) => a + b;
// call it
let res = addition_2(1, 2); // res = 3
const multiply = (x, y) => {
  return x * y;
}
let mul = multiply(3, 3); // mul = 9
```

## Object
Objects are special constant variable types. You can group specific variables together which constructs a hole logical unit.  
Like mathematical constants:
```js
const mathConstants = {
  PI: 3.1415,
  E: 2.73
};
```
You can also specify functions in an object since, functions are also variables:
```js
const math = {
  PI: 3.1415,
  E: 2.73,
  perimeter : function(R) {
    return 2 * R * this.PI;
  }
};
```
You can refer to an object by its name (just like any variable):
```js
// And you can access its properties or member variables by a '.' character
math.PI;
let p = math.perimeter(2); // p = 2 * 2 * 3.1415 = 12.56
```
You could also see the work "`this`". "`this`" is a reserved keyword in JS. Just like `let`, `const` or `function`.  
"`this`" refers to the owner of the scope, in which it can be found. E.g.: You can find a "`this`" in the scope of `math`. 
Therefore, "`this`" is basically `math`, because `math` is the owner of the scope in which the related "`this`" keyword can be found.

## Class
Class is a special type of variable. I promise this is the last type xd.  
This is the last type, because it can be kinda anything you want. You can define it whatever you would like to, since it is a **template** or **blueprint** or factory of an object. (like a shoemaker's cleat)  

How? 
### Why? Why do we need this at all?  
In some projects, which are more complex than a "Hello world!" one, you would probably need to implement many things.
E.g.: in a game or in a store, you might need to have fruits to be sold. You want to have multiple ones so, you start to implement them one by one. You start to specify their type, color, price, taste, shape, etc. After the 3nd fruit implementation you realize that your code structure is pretty similar fruit by fruit and start to think... Hmmm; Isn't there a way to merge all of these properties and call them at once when it's needed?  
And yes, there is a way! It is called a `class`. It's like creating your own building blocks from your childhood.  

### How?
You can see the syntax below in the example. (Syntax is a set of rules in any language which determine how it looks like and works.)  Keyword `class` annotates JS interpreter that a custom type definition shall start by a specifying a class name (`Fruit`) and its scope.  
You ask JS interpreter to create a class instance aka an object for you. This "request" starts with the keyword `new`. After this, you need to specify the name of the class, you want to instantiate.  
A class is a collection of variables, which can be any variable type: float, string, function, class...  
You have the choice to define a special function into your class definition called the `constructor`. 
This function is always executed, when an object is instantiated from the class definition. Through the `constructor`, you can initiate the properties (aka member variables) of the class. This is nothing special, just a function, to which you can pass parameters...  
But not like this:
```js
constructor("Apple", 10, "Red")
```
But like this:
```js
new Fruit("Apple", 10, "Red");
```
By this, constructor shall get your passed parameters and you can use it to define your properties.  

You can also define member function of a class as you can see below and you can reach it by the name of the class instance (or object).

```js
<!DOCTYPE html>
<html>
<body>

<p id="demo"></p>

<script>

class Fruit {
  constructor(type, volume, color) {
    this.type = type;
    this.volume = volume;
    this.color = color;
  }
  
  bite() {
  	this.volume -= 1;
  }
};

const init_type = "Mango";
// Instantiate (create) a new fruit object
const fruit = new Fruit(init_type, 10, "Yellow");
// Get volume of brand-new fruit
const volume_before_bite = fruit.volume;
// Cheat the game to get an apple
fruit.type = "Apple";
// Let's bite it!
fruit.bite();
// Yam yam
fruit.bite();
// Yam
fruit.bite();
// Let's see what's left from our Fruit instance called fruit
const volume_after_some_bite = fruit.volume;

const bites = volume_before_bite - volume_after_some_bite;

document.getElementById("demo").innerHTML = "User bit " + bites + " times the fruit which is a " + fruit.type + "!";

</script>

</body>
</html>
```

## Loops
Loops are special range of codes defined by a {scope} just like functions. But here the code in the curly bracket is executed again and again until the condition of the loop becomes false.  
There are 2 types of loops defined by keyword `for` and `while`. You can define your "running" condition after these keywords. Also, from any loop, you can escape by the reserved word `break`, regardless of the state of the condition after `for` or `while`.

### for
You can create a for loop by giving it 3 optional expressions in round brackets, separated by ";"s.  
 - First shall be executed before the first execution of the code within the scope of the loop
 - The second expression is the condition and shall be evaluated before each potential execution of the code in the for loop. If it is false, the next iteration is skipped and other code can run after the loop.
 - The third one is executed after every execution of the code of the loop.  

Examples:
```js
// Add numbers from 1 to 5
let sum = 0;
for (let i = 1; i <= 5; i++) {
  sum += i;
} // sum is 15 now
```

```js
// Add numbers from 1 to 5, 3 times
sum = 0;
for (let k = 0; k < 3; k++) {
  for (let i = 1; i <= 5; i++) {
    sum += i;
  }
} // sum is 45 now
```

```js
// Define multiple variables at init
let sum = 0;
const partial_results = [5];
for (let i = 0, j = 1; j <= 5; i++, j++) {
  sum += j;
  partial_results[i] = sum;
}
// now partial_results = [1, 3, 6, 10, 15] and sum = 15
```

```js
// Infinite loop
for (;true;) {
  // Add your infinitely executed code here
}
```

```js
// Break the infinity loop
for (let i = 0; true; i++) {
  if (i > 5):
    break;
}
```

#### for - of
Used to iterate over the values of an iterable object, such as arrays and strings.
```js
const l = ["Hello there!", "General Kenoby!"];
let text = "";

for (let x of l) {
  text += x + "<br>";
}
```

#### for - in
Used to iterate over the enumerable properties of an object.
```js
  // text shall be: At 1700590481 the position of the vehicle is__x = 0.31__y = 0.55__z = 4.1
const message = {timestamp: 1700590481, pos: {x: 0.31, y: 0.55, z: 4.1}}; 

let text = `At ${message.timestamp} the position of the vehicle is`;
for (let c in message.pos) {
  text += `__${c} = ${message.pos[c]}`;
}
```

### while
While is the same as for but you only have to define the condition.
```js
// Game Loop
while (true)
{
  let exit = processInput();
  if (exit):
    break;
  update();
  render();
}
```

#### do - while
```js
// series shall be [6]
let series = [];
let i = 6;
do {
  series.push(i);
  i++;
}
while (i < 3); 
```

## Conditional statements (if-else & switch)
Live with us through a beautiful year by using the following fantastic state machine:
```js
<!DOCTYPE html>
<html>
<body>

<p id="demo"></p>

<script>
 const Seasons = {
 	Summer: "Summer",
 	Autumn: "Autumn",
 	Winter: "Winter",
 	Spring: "Spring"
 }
 
let state = Seasons.Summer;
let test;

for (let i = 0; i < 4; i++) {
  switch (state) {
    case Seasons.Summer: {
      text = "Summer started; ";
      // Do something during Summer
      text += "Summer past; ";
      state = Seasons.Autumn;
      break;
    }
    case "Autumn": {
      text += "Autumn started; ";
      // Do something during Autumn
      text += "Autumn past; ";
      state = Seasons.Winter;
      break;
    }
    case Seasons.Winter: {
      text += "Winter started; ";
      // Do something during Winter
      text += "Winter past; ";
      state = Seasons.Spring;
      break;
    }
    case "Spring": {
      text += "Spring started; ";
      // Do something during Spring
      text += "Spring past; ";
      break;
    }
    default:
      text = "unknown season";
  }
}
document.getElementById("demo").innerHTML = text;
</script>

</body>
</html>
```