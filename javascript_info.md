# INTRODUCTION

- JavaScript scripts (programs that are provided and executed as plain text 
  without compilation) can be from inside HTML documents (automatically as 
  the page loads) or on any device that has a JavaScript engine (the 
  browser's engine is called JavaScript Virtual Machine, codenamed 
  differently such as V8 for Chrome, SpiderMonkey for Firefox, etc.)
- Engines (embedded in the browser) reads ("parses") the script, converts 
  ("compiles") the script to machine code, and runs it compiled code
- JavaScript's capabilities greatly depend on the environment it's running 
  in. In the browser, its capabilities are limited to protect the user's 
  safety by preventing an evil webpage from accessing private information or 
  harming the user's data:
  - Access to "local storage" is allowed, but no direct access to OS function or read/write file capabilities
  - Different tabs or windows generally do not know about each other (except 
    when one window uses JavaScript to open another one, but in accordance 
    with "Same Origin Policy" JavaScript from one page cannot access the 
    other page if they come from different domains, ports or protocols)
- There are lots of new languages which are transpiled (converted) to 
  JavaScript before they run in the browser (such as TypeScript)

# JAVASCRIPT FUNDAMENTALS

## HELLO WORLD

- Insertion into HTML using `<script>` tag
```html
<!DOCTYPE html>
<head>
    <title>Demo</title>
</head>
<body>
    <script>
            alert("Hello World");
    </script>
</body>
```
- Using `<script>` tags with `src` attributes to specify the path to the JS file
```html
<script src="/js/script1.js"></script>
<script src="/js/script2.js"></script>
```
  - The browser will download the script and store it in its cache. If other 
    pages use the same script they will take it from the cache instead of 
    downloading it again, thus reducing traffic and making pages load faster
  - If `src` attribute is set, any JavaScript inside the `<script>` tag will 
    be ignored

## CODE STRUCTURE

- JavaScript interprets line break as an implicit semicolon - This is called 
  automatic semicolon insertion
- Put semicolons between statements even if they are separated by newlines
- Single line comments - `//`
- Multiline comments - `/*...*/` (Nested multiline comments are not supported)

## THE MODERN MODE USE STRICT

- Enable modern modifications introduced as part of ECMAScript standards by 
  using `"use strict"` at top of any JavaScript file
- If you use it at top of any JavaScript function, it will be enabled just 
  for that function
- Once we start using classes and modules, this won't be further necessary
- If you place it at a line x, it will not be enabled for code present 
  within lines 0 to x-1

## VARIABLES

- Use `let` instead of `var` to create variables
- Multiple variables are to be declared in multiple statements in different 
  lines
```javascript
let first_name = "Rahul";
let last_name = "Singh";
let age = 25;
```
- Variable names can contain only letters, digits, `$` and `_`, and the 
  first character cannot be a digit, they cannot be reserved words (like 
  `let`, `const`, `class`, etc.) and be meaningful of their job
  - Multiword variables use camelCase
- Use `const` for declaring constants
  - UPPERCASE with underscores names are to be used as aliases for hard 
    coded values
  - Runtime evaluated constants will have normal variable names

## DATA TYPES

- The type of a value can be of 8 types in JavaScript
- JavaScript is "dynamically typed" - so there exists data types but they 
  are bound to the value and not the variable referencing that value
  - Number - Integer or floating-type, can be operated upon by arithmetic 
    operators, special numeric values are `Infinity`, `-Infinity` 
    (representing a number greater than any number) and `NaN`
  - BigInt - Used to represent integers of arbitrary length
  - String - Anything surrounded by quotes (`` - extended functionality quotes,
    '', "" - normal quotes)
  - Boolean - Has only 2 values (`true` and `false`)
  - Null - Reference to a non-existing object (similar to null pointer) 
    meaning nothing, empty or unknown value
  - Undefined - Meaning value is not assigned. Its possible to assign 
    undefined to a variable (but not recommended) - use null instead
  - Objects and Symbols - Objects are used to store collections of data; The 
    Symbol type is used to create unique identifiers for objects
- `typeof` operator returns the type of the operator

```javascript
// dynamic typing
let message = "hello";
message = 12345;

let n = 123;
n = 12.4325;
alert(1/0);     // Infinity
alert(Infinity);    // Infinity
alert("hello" / 2); // NaN
alert(NaN + 1);     // NaN - sticky
alert(NaN ** 0);    // 1 (exception)

const binInt = 123456n; // BigInt

let nameFieldChecked = true;    // Boolean
alert(nameFieldChecked);

let age;        // undefined
let age = null; // age has empty value
age = undefined;// possible but not recommended

typeof null;    // object - recognised as error of typeof
typeof alert;   // function - even though functions belong to the object type
typeof Math;    // object - Math is a built-in object
```

## INTERACTION - ALERT, PROMPT AND CONFIRM

- Functions to interact with user:
  - `alert` - Shows a message inside a modal window and waits for the user to 
    press Ok (meaning the visitor can't interact with the rest of the page 
    until they have dealt with the window)
  - `prompt` - It shows a modal window with a text message (`title`), an input 
    field for the visitor, and the buttons OK/Cancel -> The visitor can type 
    something in the prompt input field to get the text as result, or press 
    Cancel to get `null` as the result
  - `confirm` - Shows a modal window with a question and Ok and Cancel 
    options -> The result is true if press Ok or false if press Cancel

```javascript
alert("Hello");

// result = prompt(title, [default]);
let age = prompt("How old are you?", "Enter age as a number");
alert(`You are ${age} years old!`);

let isBoss = confirm("Are you the boss?");
alert(isBoss);
```

## TYPE CONVERSIONS

- `alert` converts any type to string in order to display it
- Mathematical operators convert values to numbers
- Explicit conversion is required when we read a value from a string-based 
  source like a text form but expect a number to be entered. If string is 
  not a valid number, the result of such a conversion is `NaN`
  - `undefined` -> `NaN`
  - `null` -> 0
  - `true`, `false` -> 1, 0
  - `string` -> Whitespace from the start and end are removed. If string is 
    left then the Number or `Nan`; if string is not left then 0
- Boolean conversion happen in logical operations `Boolean(value)`
  - Empty values (0, `null`, `undefined`, `NaN`, `false`) become false, else 
    true
```javascript
// String conversion
let value = true;
value = String(value);  // "true"

// Numeric Conversions
alert("6" / "2");   // 3, strings are converted to numbers
let num = Number("123");    // explicit conversion to Number type 
```

## BASIC OPERATORS, MATHS

```javascript
let s = "my" + " string";   // concatenation
```

## FUNCTION EXPRESSIONS

- In JavaScript a function is a special kind of value
- Function expressions allow us to create a function that in the middle of 
  an expression
- Omitting the name of function expression is valid
- Its mostly used when we need to create a function and immediately call it, 
  or schedule for a later execution, not stored anywhere, thus remaining 
  anonymous
```javascript
let sayHi = function() {
    alert("hello");
};
// sayHi variable gets a value (the new function)
// name of the function has been omitted - rather the function expression is 
// assigned to a variable directly after its creation
```

- Since a function is a value in JavaScript (whose value is its body)
```javascript
function sayHi() {
    alert("hello");
}
alert(sayHi);   // shows the function's code rather than running it
                // to run a function call it using parentheses

let func = sayHi;   // copying "values"
func();         // output -> hello
```

- Function expressions have semicolon at the end because they are part of an 
  assignment statement `let func = function() {};`, and its recommended to 
  put semicolons at the end of statements, but not function syntax

### CALLBACK FUNCTION

```javascript
function ask(question, yes, no) {
    if (confirm(question)) yes()
    else no();
}

function showOk() {
    alert("You agreed");
}
function showCancel() {
    alert("You cancelled the execution");
}

// usage: functions showOk, showCancel are passed as arguments to ask
ask("Do you agree?", showOk, showCancel);

// Using function expressions this code becomes smaller
ask(
    "Do you agree?",
    function() { alert("You agreed."); },
    function() { alert("You cancelled the transaction"); }
);
```

- The arguments `showOk` and `showCancel` are referred to as Callback 
  functions or just Callbacks. The idea is that we pass a function, and we 
  expect it to be "called back" later if necessary

## ARROW FUNCTIONS

- Better than Function Expressions
- Without curly braces - `(...args) => expression` -> The function
  evaluates the right side expression and returns the result. Parentheses
  can be omitted if there's only a single argument `n => n * 2`
```javascript
// let func = (arg1, arg2, ..., argn) => expression
// Equivalent function expression
/*
let func = function(arg1, arg2, ..., argn) {
    return expression;
}
*/

let sum1 = (a, b) => a + b;
let sum2 = function (a, b) {
  return a + b;
};

let double = n => n * 2;
// Equivalent function expression
let double2 = function (n) {
  return n * 2;
};

let sayHi = () => alert("Hello!");
sayHi();
```

- Arrow functions can be used in the same way as Function Expressions -> to
  dynamically create a function
```javascript
let age = prompt("What is your age?", 18);

let welcome = age < 18 ? () => alert("Hello!") : () => alert("Greetings!");

welcome();
```

### MULTILINE ARROW FUNCTIONS

- With curly braces - `(...args) => { body }` -> Brackets allow us to write
  multiple statements inside the function but we need an explicit
  `return` to return something
```javascript
let sum = (a, b) => {
  // the curly braces opens a multiline function
  let result = a + b;
  return result; // if we need curly brances, then we need an
  // explicit "return"
};
```

### SUMMARY

- Arrow functions are handy for simple one-liner actions. They are of two types:

# CODE QUALITY
# OBJECTS: THE BASICS

##  OBJECTS

- Objects are used to store keyed collections of various data and more 
  complex entities
- An object can be created with figure brackets `{...}` with an optional 
  list of properties
- A property is a "key: value" pair, where `key` is a string (property name) 
  and `value` can be anything
```javascript
let user = new Object();    // "object contructor" syntax
let user2 = {};             // "object literal" syntax - recommended

let user3 = {
    name: "John",   // by key "name" store value "John"
    age: 30         // by key "age" store value 30
};

// get property values of the object using dot notation
alert(user.name, user.age);     // John, 30

// add property value to the object
user.isAdmin = true;

// remove property from the object using delete operator
delete user.age;
```

### PROPERTY NAME LIMITATIONS

- 

### PROPERTY EXISTENCE TEST USING IN OPERATOR

- `in` operator is present to handle an explicit case where a property's 
  value is `undefined` (this is discouraged and `null` should be used for 
  unknown and empty values)
```javascript
let obj = {
    "name": undefined,
    "age": 42,
};

alert(obj.age);     // 42
alert(obj.blabla);  // undefined - not present in object
alert(obj.name);    // undefined - so what does this mean - value is present 
// or not
alert("name" in obj);   // false - means not present
```

### THE FOR-IN LOOP

- Used to loop over all the keys of an object
```javascript
let user = {
    name: "John",
    age: 30,
    isAdmin: true,
};

for (let key in user) { // looping variable name prop is widely used
    // keys
    alert(key);         // name, age, isAdmin
    // values for the keys
    alert(user[key]);   // John, 30, true
}
```

- Objects are ordered in a special way - Integer properties are sorted, 
  others appear in creation order
- Integer properties are strings that can be converted to-and-from an 
  integer without a change. So `"49"` is an integer property, but `"+49"` and 
  `"1.3"` are not
```javascript
let codes = {
    "49": "Germany",
    "41": "Switzerland",
    "44": "Great Britain",
    "1": "USA"
};
for (let code in codes) {
    alert(code);    // 1, 42, 43, 44
}

let codes = {
    "+49": "Germany",
    "+41": "Switzerland",
    "+44": "Great Britain",
    "+1": "USA"
};
for (let code in codes) {
    alert(+code);   // 49, 41, 44, 1    
}
```


# DATA TYPES



# ADVANCED WORKING WITH FUNCTIONS

# OBJECT PROPERTIES CONFIGURATION

# PROTOTYPES, INHERITANCE

# CLASSES

# ERROR HANDLING - TODO: CUSTOM ERRORS WHOLE CHAPTER (SINCE IT CONTAINS CLASSES)

## ERROR HANDLING USING TRY...CATCH

- `try...catch` allows us to "catch" runtime errors so the script can, 
  instead of dying, do something more reasonable (so it must be a 
  syntactically correct JavaScript program - it should not have any 
  "parse-time" errors which occur when JavaScript engine first reads the code)
```javascript
try {
    // code
    // if no error found then try block is executed and catch block is skipped
} catch (err) {
    // error handling
    // if error found then err will contain the error object
}
```

- `try...catch` works synchronously and it won't catch errors in asychronous 
  code (because the function itself is executed later after the engine has 
  already left the try-catch construct)
```javascript
// to handle async code the try-catfch must be inside the function
/*
try {
    setTimeout(function() {
        noSuchVariable;
    }, 1000);
} catch (err) {
    alert ("wont work");
}
*/
setTimeout(function() {
    try {
        noSuchVariable; // try...catch handles this error 
    } catch {   // if you don't need error details catch can omit it
        alert(" error is caught here!"); 
    }
}, 1000);
```

### ERROR OBJECT

- When an error occurs, JavaScript generates an object containing the 
  details about it, which is then passed as an argument to `catch`
- Error object has two main properties - `name` and `message`, `stack`

### THROWING OUR OWN ERRORS

- Use the `throw` operator
```javascript
throw <error_object>
// error_object can even be primitives, but prefer using an object with a 
// name and message property for compatibility reasons
// JavaScript provides in-built error_objects like Error(message), 
// SyntaxError(message), ReferenceError(message), TypeError(message)
let error = new Error("Things Happen :(");
```

### RETHROWING

- Catch should only process errors it knows, and rethrow all others
- Rethrowing technique:
  - catch gets all errors
  - In the `catch(err) {}` block we analyze the error object `err`
  - If we don't know how to handle it we do `throw err`
```javascript
function readData() {
    let json = `{ "age": 30 }`; // incomplete data

    try {
        let user = JSON.parse(json);
        if (!user.name) {
            throw new SyntaxError("Incomplete data: No name");
        }
        blabla();   // unexpected error which isn't present in our catch block
        alert(user.name);
    } catch (err) {
        if (err instanceof SyntaxError) {   // if we get incorrect data then handle
            alert("JSON Error: " + err.message);
        } else {    // for any other issues we might encounter rethrow the error
            throw err;  // rethrow (*) 
        }
    }
}

try {
    readData();
} catch(err) {
    alert("External catch got: " + err); // caught any other errors
}
```

### TRY...CATCH...FINALLY

- `finally` is used to execute always (even if there] is a `return` statement 
  present inside of `try` and it gets executed just before the `return`) 

### GLOBAL CATCH

- JavaScript environments provide functions for logging uncaught errors. For 
  e.g. NodeJS provides `process.on("uncaughtException)` and in the browser 
  we can assign a function to the `window.onerror` property which will run 
  in case of an uncaught error
```javascript
window.onerror = function(message, url, line, col, error) {}
// message - Error message
// url - path of the script where error happened
// line, col - where error happened
// error - Error Object
```
- Web services provide error-logging functionality as well which provide a 
  JS script to insert on pages (which sets a custom `window.onerror` 
  function), and if an error occurs, the script sends a network request to 
  the service about it. We can log into the service and see the error (for e.
  g. https://errorception.com or https://www.muscula.com)

## CUSTOM ERRORS, EXTENDING ERRORS

- 

# PROMISES, ASYNC/AWAIT - TODO - WHOLE OF JAVASCRIPT BEFORE THIS PART (TOUGH)

## INTRODUCING CALLBACKS

- JavaScript host environments allow you to schedule asynchronous actions 
  (tasks that initiate now but finish later). For e.g. `setTimeout`

## PROMISE

## PROMISES CHAINING

## ERROR HANDLING WITH PROMISES

## PROMISE API

## PROMISIFICATION

## MICROTASKS

## ASYNC / AWAIT

# GENERATORS, ADVANCED ITERATION

# MODULES

- A JavaScript file is a module containing a class or a library of functions 
  for a specific purpose. They are combined to form an application
- `export` - labels variables and functions that should be accessible from 
  outside the current module
- `import` - allows the import of functionality from other modules
```javascript
// sayHi.js
export function sayHi(user) {
    alert(`Hello, ${user}`);
}

// main.js
import {sayHi} from "./sayHi.js";

alert(sayHi);   // function
sayHi("John");
```
