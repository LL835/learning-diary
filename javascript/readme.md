# Javascript
- [Arrays](#arrays)
	* [Push and pop](#push-and-pop)
	* [For each](#for-each)
	* [Slice](#slice)
	* [Map](#map)
	* [Join](#join)
- [Testing](#testing)
	* [Equals](#equals)
	* [Not equals](#not-equals)
	* [Grouping tests](#grouping-tests)
	* [Making code easier to test](#making-code-easier-to-test)
	* [Deep equality](#deep-equality)
- [URLSearchParams](#urlsearchparams)
	* [Constructing a new URLSearchParams object](#constructing-a-new-urlsearchparams-object)


---
## Arrays
Arrays are sequences of values that have a specific order and a length.

```js
const arr = [1, 2, 3];
return arr.length; /* 3 */
```

Retrieve values from an array using `[]`. Indexes start at 0.

```js
const arr = [1, 2, 3];
return arr[0] /* 1 */
```

If the index is not in the array, the returned value is `undefined`.

```js
const arr = [1, 2, 3];
return arr[203] /* undefined */
```

Change a value in an array with `[]` and `=`. 
```js
const arr = [1, 2, 3];
arr[0] = 'abc' /* the array is now ['abc', 2, 3]*/
return arr[0] /* 'abc' */
```
### Push and pop
Add elements to the end of an array with `push`.

```js
const arr = [1, 2];
arr.push(3);
return arr /* [1, 2, 3] */
```

`push` returns the array's length, including the newly-pushed element.

```js
const arr = [1, 2];
return arr.push(3); /* 3 */
```

Remove the last element of an array with `pop`.

```js
const arr = [1, 2];
arr.pop();
return arr /* [1] */
```

`pop` returns the element that was removed.

```js
const arr = [1, 2];
return arr.pop(); /* 2 */
```

`pop` returns `undefined` if the array is empty.

```js
const arr = [];
return arr.pop() /* undefined */
```

`pop` and `push` change the array (instead of returning a new array).

```js
const arr = [1, 2, 3, 4];
arr.push(5);
return arr /* [1, 2, 3, 4, 5] */
```


```js
const arr = [1, 2, 3, 4];
arr.pop();
return arr =  /* [1, 2, 3] */
```

### For each
`forEach` executes a function once for each element in an array. `forEach` is similar to a `for` loop. 

```js
const arr = [1, 2, 3];
let sum = 0;
arr.forEach(x => {
	sum += x;
});
return sum /* 6 */
```

The second argument for `forEach`'s callback is the item's index.

```js
const arr = [1, 3, 5];
let result = '';
arr.forEach((x, index) => {
	result += x + (arr[index] + 1).toString()
})
return sum /* '123456' */
```
### Slice
Split an array into a shorter array with `slice`.

The first argument is the index to start slicing the array from.

```js
const arr = [1, 2, 3, 4, 5];
return arr.slice(1); /* [2, 3, 4, 5] */
```

If the index is larger than the size of the array, `slice` returns an empty array. 

```js
const arr = [1, 2, 3, 4, 5];
return arr.slice(10); /* [] */
```

The second argument is the index to stop slicing at. The element at the given index will not be included in the sliced array. This argument is optional.

```js
const arr = [1, 2, 3, 4, 5];
return arr.slice(1, 4); /* [2, 3, 4] */
```

Slicing past the end of an array is the same as slicing up to the last element.

```js
const arr = [1, 2, 3, 4, 5];
return arr.slice(1); /* [2, 3, 4, 5]*/
return arr.slice(1, 400); /* [2, 3, 4, 5] */
```

If no arguments are given, `slice` returns a copy of the array.

### Map
Use `map` to call a function on each element in an array and return a new array with the values returned from those function calls. The original may is not changed by `map`.

```js
const arr = [1, 2, 3];
return arr.map(x => x * 10) /* [10, 20, 30] */
```

### Join
`join` combines elements in an array together into a string.
```js
const arr = ['a', 'b', 'c'];
return arr.join('') /* 'abc' */
```

If no argument is given to `join`, the strings are joined by `,` by default.

```js
const arr = ['a', 'b', 'c'];
return arr.join() /* 'a,b,c' */
```

The argument can be any string.

```js
const arr = ['a', 'b', 'c'];
return arr.join('x') /* 'axbxc' */
```

`null` and `undefined` become empty strings when joined.

```js
const arr = [null, 'b', undefined];
return arr.join() /* ' ,b, ' */
```
---
## Testing
Testing in software development is the process of finding out whether the code does what it is supposed to do.

Testing can be done manually with `console.log()`. Alternatively, it can be automated.

#### Equals
One way to automate this is to write an equals function.

```js
function equal(actual, expected) {
	if (actual === expected) {    
		console.info(`Pass: Expected ${expected} and received ${actual}`);  
	} else {
	    console.error(`Fail: Expected ${expected} but received ${actual} instead`);  
	}
}

const result1 = square(2);
const expected1 = 4;
equal(result1, expected1); // `"Pass: Expected 4 and received 4`.
const result2 = square(3.5);
const expected2 = 9999; // `Fail: Expected 9999 but received 12.25 instead"`.
```

### Not equals
A not-equals function can also be helpful in testing.

```js
function notEqual(actual, expected) {
	if (actual !== expected) {
	    console.info(`Pass: ${expected} is different to ${actual}`);  
	} else {
	    console.error(`Fail: ${expected} is the same as ${actual}`);  
	}
}
const result3 = square(3);
const expected3 = 10;
notEqual(result3, expected3); // `"Pass: 10 is different to 3"`
```

### Grouping tests
Group tests together with a separate test function.  

```js
function test(name, testFunction) {
	console.group(name); // creates a new group name. All console messages below this line below to this group now
	testFunction();
	console.groupEnd(); // closes the group
}

test("Correctly squares integers", () => {
	const result = square(2);  
	const expected = 4;  
	equal(result, expected);
	}); // `"Pass: Expected 4 and received 4`

test("Correctly squares decimals", () => {  
	const result = square(3.5);
	const expected = 12.25;
	equal(result, expected);
	}); // "Pass: Expected 12.25 and received 12.25"
```

### Custom messages
Make the testing functions simpler to understand by adding an option for a custom message.

```js
function equal(actual, expected, message) {
	if (actual === expected) {    
		const defaultMessage = `Expected ${expected} and received ${actual}`;
		console.info("Pass: " + (message || defaultMessage));
	} else {
	    const defaultMessage = `Expected ${expected} but received ${actual} instead`;
	    console.error("Fail: " + (message || defaultMessage));  
	}
}

test("Correctly squares integers", () => {
	const result = square(2);  
	const expected = 4;
	equal(result, expected, "square(2) should return 4");
	}
); // "Pass: square(2) should return 4"
```
### Making code easier to test
Make code easier to test by:
- Writing functions that only have a single responsibility. 
- Use pure functions (that is, functions that return the same output when given the same input)

### Deep equality
Be careful when testing objects or arrays. Objects that look the same do not necessarily equal each other.

```js
const x = { name: "oliver" };
const y = { name: "oliver" };
console.log(x === y); // false
```

One workaround is to test the specific properties inside the objects.

```js
console.log(x.name === y.name); // Logs: true
```
---
## URLSearchParams
`URLSearchParams` is an API that makes working with URL strings easier. 

### Constructing a new URLSearchParams object
Construct a new URLSearchParams object with `new URLSearchParams()`. It takes a single argument. (If no argument is given, an empty instance is created, which may be helpful in certain situations.)

The argument can be the URL query string itself.

```js
const queryString = "name=Michelle&age=29&job=Football+Coach" // raw URL string to be manipulated
const params = new URLSearchParams()
```

Or it can be an object.

```js
const params = new URLSearchParams({name= "Michelle", age = 29, job = "Football Coach"})
```

URLSearchParams have access to lots of different methods, including:

- `get`.
- `set`.
- `toString`.
