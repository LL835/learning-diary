# Javascript
- [Arrays](#arrays)
	* [Push and pop](#push-and-pop)
	* [For each](#for-each)
	* [Slice](#slice)
	* [Map](#map)
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
