# hello nice yes hello

>>> [some markdown stuff](http://assemble.io/docs/Cheatsheet-Markdown.html#named-anchors)

##### statements
###### [control flow](#control flow)
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
[`async function`](#async function)
[`return`](#return)
[`class`](#class)
###### [iterations](#iterations)
[`do...while`](#do...while)
[`for`](#for)
[`for each...in`](#for each...in)
[`for...in`](#for...in)
[`for...of`](#for...of)
[`for await...of`](#for await...of)
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

- _optional_ `default`


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
