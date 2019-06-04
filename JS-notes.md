# hello nice yes hello

>>> [> some markdown stuff](http://assemble.io/docs/Cheatsheet-Markdown.html#named-anchors)

##### statements
###### [control flow](#control-flow)
[`Block`](#Block)
[`break`](#break)
[`continue`](#continue)
[`Empty`](#Empty)
[`if...else`](#if...else)
[`switch`](#switch)
[`throw`](#throw)
[`try...catch`](#try...catch)
###### [declarations](#declarations)
[`var`](#var)
[`let`](#let)
[`const`](#const)
###### [functions](#functions)
[`function`](#function)
[`function*`](#function*)
[`async function`](#async-function)
[`return`](#return)
[`class`](#class)
###### [iterations](#iterations)
[`do...while`](#do...while)
[`for`](#for)
[`for each...in`](#for-each...in)
[`for...in`](#for...in)
[`for...of`](#for...of)
[`for await...of`](#for-await...of)
[`while`](#while)
###### [others](#others)
[`debugger`](#debugger)
[`export`](#export)
[`import`](#import)
[`import.meta`](#import.meta)
[`label`](#label)
`with 🤮`

##### [array methods](#array-methods)
[`filter`](#filter)
<br/>...

## control flow

### Block

`{ }` Used to group zero or more statements. Delimited by a pair of curly brackets (curly bois).

```javascript
{
  StatementList
}
```
`var` does **not** have block scope!!<br/>
`let` and `const` **do** have block scope

```javascript
foo('outside');  // TypeError: foo is not a function (no hoist!!)
{
  function foo(location) {
   console.log('foo is called ' + location);
  }
  foo('inside'); // works correctly and logs 'foo is called inside'
}
----------------------------------------------------
foo;  // returns undefined (implicit variable declaration is hoisted)
{
  function foo(location) {
   console.log('foo is called ' + location);
  }
  foo('inside'); // works correctly and logs 'foo is called inside'
}
----------------------------------------------------
{
  function foo(location) {
   console.log('foo is called ' + location);
  }
  foo('inside'); // works correctly and logs 'foo is called inside'
}
foo('outside');  // works correctly and logs 'foo is called outside'
```
### `break`

Terminates current loop, transfers control to following statement.

This terminates the `while` loop when `i` is 3:

```javascript
function testBreak(x) {
  var i = 0;

  while (i < 6) {
    if (i == 3) {
      break;
    }
    i += 1;
  }

  return i * x;
}
```

A `break` statement cannot be used within the body of a function that is itself nested within the current loop, switch, or label statement that the break statement is intended to break out of.

```javascript
block_1: {
  console.log('1');
  break block_2; // SyntaxError: label not found
}

block_2: {
  console.log('2');
}
----------------------------------------------------
function testBreak(x) {
  var i = 0;

  while (i < 6) {
    if (i == 3) {
      (function() {
        break;
      })();
    }
    i += 1;
  }

return i * x;
}

testBreak(1); // SyntaxError: Illegal break statement
```

### `continue`

Terminates execution of the statements in the current iteration of the current loop, and continues execution of the loop with the next iteration.

- in a `while` loop - jumps back to the condition
- in a `for` loop - jumps to the update expression

```javascript
var i = 0;
var n = 0;

while (i < 5) {
  i++;

  if (i === 3) {
    continue;
  }

  n += i;
}
n;  // takes values 1, 3, 7, 12
```

### Empty

`;`

The empty statement is a semicolon - indicating that no statement will be executed, even if JavaScript syntax requires one. The opposite of a block statement.

```JavaScript
var arr = [1, 2, 3];

// Assign all array values to 0
for (i = 0; i < arr.length; arr[i++] = 0) /* empty statement */ ;

console.log(arr)
// [0, 0, 0]
```

> **Note:** It is a good idea to comment the intentional use of the empty statement, as it is not really obvious to distinguish between a normal semicolon.

### `if...else`

Executes a statement if a condition is truthy.

```JavaScript
if (condition)
   statement1
[else
   statement2]
```

- `condition` an expression evaluated to truthy or falsy

- `statement1` executes if condition is truthy. can be any statement

- `statement2` executes if condition is falsy and the `else` clause exists

Remember your truthies and falsies!

#### `false`  `undefined` `null` `0` `-0` `NaN` `"" (empty string)`  
 are the only falsy values.

Can be chained together:

```JavaScript
if (condition1)
  statement1
else if (condition2)
  statement2
else if (condition3)
  statement3
...
else
  statementN
```

**Note:** there is no elseif (in one word) keyword in JavaScript.

To execute multiple statements within a clause, use a block statement (`{...}`). It is good practice to always use block statements, especially with nested `if` statements.

Generally discouraged, but if you _need_ to use an assignment in a conditional expression, a common practice is to put additional parentheses around the assignment. For example:

```JavaScript
if ((x = y)) {
  /* do the right thing */
}
```

### `switch`

Evaluates an expression, matching the expression's value to a `case` clause, and executes statements associated with that case, as well as statements in cases that follow the matching case.

```JavaScript
switch (expression) {
  case value1:
    //Statements executed when the
    //result of expression matches value1
    [break;]
  case value2:
    //Statements executed when the
    //result of expression matches value2
    [break;]
  //...
  case valueN:
    //Statements executed when the
    //result of expression matches valueN
    [break;]
  [default:
    //Statements executed when none of
    //the values match the value of the expression
    [break;]]
}
```

- `expression` the result of which is matched against each case clause

- _optional_ **`case valueN`** if `expression` matches the specified `valueN`, the statements inside the case clause are executed until either the end of the switch statement or a `break`

- _optional_ `default` executed if none of the `case` clauses match the `expression`

**Remember:** if break is omitted, the program continues execution at the next statement in the switch statement.

```JavaScript
var expr = 'Papayas';
switch (expr) {
  case 'Oranges':
    console.log('Oranges are $0.59 a pound.');
    break;
  case 'Mangoes':
  case 'Papayas':
    console.log('Mangoes and papayas are $2.79 a pound.');
    // expected output: "Mangoes and papayas are $2.79 a pound."
    break;
  default:
    console.log('Sorry, we are out of ' + expr + '.');
}
```

Multi-case (taking advantage of missing-`break` statement behavior):
```JavaScript
var Animal = 'Giraffe';
switch (Animal) {
  case 'Cow':
  case 'Giraffe':
  case 'Dog':
  case 'Pig':
    console.log('This animal will go on Noah\'s Ark.');
    break;
  case 'Dinosaur':
  default:
    console.log('This animal will not.');
}
```

Block-scope variables in `switch`:

```JavaScript
const action = 'say_hello';
switch (action) {
  case 'say_hello':
    let message = 'hello';
    console.log(message);
    break;
  case 'say_hi':
    let message = 'hi';
    console.log(message);
    break;
  default:
    console.log('Empty action received.');
    break;
}
// Uncaught SyntaxError: Identifier 'message' has already been declared
```

Fixed with enclosing brackets:

```JavaScript
const action = 'say_hello';
switch (action) {
  case 'say_hello': { // added brackets
    let message = 'hello';
    console.log(message);
    break;
  } // added brackets
  case 'say_hi': { // added brackets
    let message = 'hi';
    console.log(message);
    break;
  } // added brackets
  default: { // added brackets
    console.log('Empty action received.');
    break;
  } // added brackets
}
// hello
```

- [switch statement multiple cases (stack overflow)](http://stackoverflow.com/questions/13207927/switch-statement-multiple-cases-in-javascript)

### `throw`

The `throw` statement throws a user-defined exception. Execution of the current function will stop and control will be passed to the first `catch` block in the call stack. If no `catch` block exists among caller functions, the program will terminate.

```javascript
throw _expression_;
```

-`expression` the expression to throw

**Note:** the throw statement is affected by automatic semicolon insertion (ASI) as no line terminator between the throw keyword and the expression is allowed.

There are some [long examples](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/throw) online.

### `try...catch`

Marks a block of statements to try, and specifies a response, should an exception be thrown.

```JavaScript
try {
  try_statements
}
[catch (exception_var_1 if condition_1) { // non-standard
  catch_statements_1
}]
...
[catch (exception_var_2) {
  catch_statements_2
}]
[finally {
  finally_statements
}]
```

- `try_statements` the statements to be executed

- `catch_statements_1` `catch_statements_2` executed if an exception is thrown in the `try` block

- `exception_var_1` `exception_var_2`  identifier to hold an exception object for the associated `catch` clause

- `condition1` a conditional expression

- `finally_statements` executed after the `try` statement completes, regardless of whether an exception was thrown or caught

`{}` must always be used with a `try` block. At least one `catch` or `finally` statement must be preset. There are three forms this might take:

  1. `try...catch`

  2. `try...finally`

  3. `try...catch...finally`

A `catch` clause contains statements that specify what to do if an exception is thrown in the `try` block. That is, you want the `try` block to succeed, and if it does not succeed, you want to pass control to the `catch` block. If any statement within the `try` block (or in a function called from within the `try` block) throws an exception, control is immediately shifted to the `catch` clause. If no exception is thrown in the `try` block, the `catch` clause is skipped.

The `finally` clause executes after the `try` block and `catch` clause(s). It always executes, regardless of whether an exception was thrown or caught.

You can nest one or more `try` statements. If an inner `try` statement does not have a `catch` clause, the enclosing `try` statement's `catch` clause is entered.

With unconditional `catch` clauses, the `catch` block is entered when _any_ exception is thrown. Conditional `catch` clauses are deprecated. :neckbeard:

If the `finally` block returns a value, this value becomes the return value of the entire `try-catch-finally` production, regardless of any `return` statements in the `try` and `catch` blocks.

```JavaScript
try {
  throw 'myException'; // generates an exception
}
catch (e) {
  // statements to handle any exceptions
  logMyErrors(e); // pass exception object to error handler
}
```

The `catch` block specifies an identifier (`e` in the example above) that holds the value specified by the `throw` statement. The `catch` block is unique in that JavaScript creates this identifier when the `catch` block is entered, and it adds it to the current scope; the identifier lasts only for the duration of the `catch` block; after the `catch` block finishes executing, the identifier is no longer available.

There's a lot more to `try...catch` but like half of it is deprecated...

Ordering:

```JavaScript
try {
  try {
    throw new Error('oops');
  }
  finally {
    console.log('finally');
  }
}
catch (ex) {
  console.error('outer', ex.message);
}

// Output:
// "finally"
// "outer" "oops"
```

```JavaScript
try {
  try {
    throw new Error('oops');
  }
  catch (ex) {
    console.error('inner', ex.message);
  }
  finally {
    console.log('finally');
  }
}
catch (ex) {
  console.error('outer', ex.message);
}

// Output:
// "inner" "oops"
// "finally"
```

## declarations

### `var`

Declares a variable, optionally initializing it to a value.

```javascript
var varname1 [= value1] [, varname2 [= value2] ... [, varnameN [= valueN]]];
```

- `varnameN` can be any legal identifier

- `valueN` initial variable value, any legal expression. default is _undefined_

Scope of variables declared with `var` is _execution context_, be it the enclosing function or global. If you redeclare a JavaScript variable, it will not lose its value. Assigning a value to an undeclared variable implicitly creates it as a global variable.

It is recommended to always declare variables at the top of their scope (the top of global code and the top of function code) so it's clear which variables are function scoped (local) and which are resolved on the scope chain.

Declaring and initializing two variables:

`var a = 0, b = 0;`

### `let`

Declares a block scope local variable, optionally initializing it to a value. Redeclaring the same variable within the same function or block scope raises a SyntaxError.

```javascript
let x = 1;
switch(x) {
  case 0:
    let foo;
    break;

  case 1:
    let foo; // SyntaxError for redeclaration.
    break;
}
```

#### `let` variables are not hoisted

Refer to the [_temporal dead zone... :skull:_](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let#Temporal_dead_zone)

```javascript
function do_something() {
  console.log(bar); // undefined
  console.log(foo); // ReferenceError
  var bar = 1;
  let foo = 2;
}
```

```javascript
function go(n) {
  // n here is defined!
  console.log(n); // Object {a: [1,2,3]}

  for (let n of n.a) { // ReferenceError
    console.log(n);
  }
}

go({a: [1, 2, 3]});
```

### `const`

Declares a block scope local variable, a value must be assigned. The value of a constant cannot change through reassignment, and it can't be redeclared.

```javascript
const name1 = value1 [, name2 = value2 [, ... [, nameN = valueN]]];
```

The `const` declaration creates a read-only reference to a value. It does **not** mean the value it holds is immutable, just that the variable identifier cannot be reassigned.

## functions



## iterations
## others

---

## Array methods

### `filter()`<a name="filter"></a>

`filter()` creates a new array with all the elements that pass the tests of a function. A `callback` is provided, accepting three arguments:

```javascript
var newArray =
arr.filter(callback(
  element[, index[, array]]
)[, thisArg])
```

- `element` current array element

- _optional_ `index` current array element index

- _optional_ `array` array filter is called on

- _optional_ `thisArg` value to use as `this`

##### Return Value

A new array with the passing elements, or an empty array.

- [x] Non-destructive

##### Examples

Removes elements with a value less than 10:

```javascript
function isBigEnough(value) {
  return value >= 10;
}

var filtered = [12, 5, 8, 130, 44].filter(isBigEnough);
// filtered is [12, 130, 44]
```
Filter an array based on search criteria: `:(`

```javascript
const fruits =
['apple', 'banana', 'grapes', 'mango', 'orange'];

const filterItems = (arr, query) => {
  return arr.filter(el => el.toLowerCase().indexOf(
    query.toLowerCase()
  ) !== -1);
};

console.log(filterItems(fruits, 'ap'));
  // ['apple', 'grapes']
console.log(filterItems(fruits, 'an'));
  // ['banana', 'mango', 'orange']
```
