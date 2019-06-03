# hello nice yes hello

## Array methods

links to methods below?

* [fffff](#abcd)

### `filter()`<a name="abcd"></a>

`filter()` creates a new array with all the elements that pass the tests of a function. A `callback` is provided, accepting three arguments:

- `element` current array element

- _optional_ `index` current array element index

- _optional_ `array` array filter is called on

- _optional_ `thisArg` value to use as `this`

```javascript
var newArray =
arr.filter(callback(
  element[, index[, array]]
)[, thisArg])
```
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

## ffffff<a name="abcd"></a>

[more markdown stuff](http://assemble.io/docs/Cheatsheet-Markdown.html#named-anchors)
