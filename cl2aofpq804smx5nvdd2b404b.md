## One-liner Solutions to 6 Coding Questions

Coding questions are an integral part of any JavaScript interview.

There is more than one approach for any question. **But, can it be done in a one-liner?**

Yes, some questions are pretty straightforward and have a clean solution in a single line of code using ES6 features.

Note that, I am no expert in coming up with such solutions and not at all guaranteeing that they are the ultimate go-to answers for any coding questions.

------

### How to remove duplicates from a sorted array?

```
const arr = [1, 2, 2, 3, 4, 4, 5];
const filterArray = arr.filter( (item, pos) => arr.indexOf(item) === pos);
console.log(filterArray);
```

-----

### Perform n left rotations in an array
```
const arr = [1, 2, 3, 4, 5];
const rotate = (arr, rotations = 1) => [...arr.slice(rotations, arr.length), ...arr.slice(0, rotations)];
console.log(rotate(arr, 1));
```
-----

### Find out the second largest element in an unsorted array
```
const arr = [9, 1, 8, 2, 3, 4, 5];
arr[arr.indexOf(Math.max(...arr))] = Math.max();
console.log(Math.max(...arr));
```
-----

### Find the sum of an array
```
const arr = [1, 2, 3, 4, 5];
const sum = arr.reduce( (acc, currentVal) => acc += currentVal, 0);
console.log(sum);
```
-----

### Convert the first letter of every word in a string in uppercase.
```
const str = "i love programming";
return str.split(" ").map((s) => s.charAt(0).toUpperCase() + s.slice(1)).join(' ');
```
-----

### Count the frequency of characters in a string
```
const s = "samplestring";
const counter = s => [...s].reduce((arr, char) => (arr[char] = arr[char]++ || 1) && arr, {});
console.log(counter);
```

----

Thank you for reading.