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
```

## Data types
Javascript numbers are always one type: double (64-bit floating point).  
IEEE 754:
- number (the fraction) is stored in bits 0 to 51
- exponent in bits 52 to 62
- sign in bit 63

```js
// Number
let a = 1.1
```

Other types:
```js
// Strings
a = "str"
// Booleans
let x = true;
// Object (detailed explanation later on)
const human = {name:"Joe", color:"white"};
// Array object (detailed explanation later on)
const cars = ["VW", "Volvo", "BMW"];
// Date object (detailed explanation later on)
const date = new Date("2022-03-25");
// None type
let x = NaN;
let y = Infinity;
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

