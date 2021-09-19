### Arrays

#### Creating Arrays

The simplst way to create an array is with square braces

```js
let numbers = [];
let numbers = new Array();
```

Arrays can also be declared with elements inside

```js
let numbers = [1,2,3,4,5];
let numbers = new Array(1,2,3,4,5);
```

Array elements don't have to be the same type.

```js
let objects = [1, "Joe", true, null];
```

To check if an object is an array, you can use **Array.isArray()**

```js
let numbers = 3;
let arr = [1,2,3,4,5];
Array.isArray(numbers) // false
Array.isArray(arr) // true
```

Array elements can be accessed using the [ ] operator and passing the index of the element. Indices are 0 based so the first element starts at index 0.

```js
let numbers = [1,2,3,4,5];
console.log(numbers[0]) // 1
console.log(numbers[4]) // 5
```

#### Creating Arrays from Strings

An array can be made from a string by calling the **split(delimiter)** function on the string. By passing a common delimiter for each word we can split our sentence into different elements.

```js
let sentence = "I really want to work at funimation";
let words = sentence.split(" "); // space is our delimiter so sentence will be broken up by the spaces.
```

#### Aggregate Array Operations

You can assign one array to another array, but this will only create a reference to the original array. Any changes made to the original will effect the copy. This is called a **shallow copy**.

```js
let nums = [1,2,3,4,5];
let samenums = nums;
nums[0] = 10;
console.log(samenums[0]) // 10
```

To make a **deep copy** it's better to read from the original arrays values and store them in the new array.

```js
let nums = [1,2,3,4,5];
let samenums = [];

nums.forEach(function(n,i){
  samenums[i] = n;
});

nums[0] = 10;
console.log(samenums[0]) // 1
```

#### Accessor Functions

**indexOf** - If the argument is contained in the array, returns the index for the argument. If the argument is not found then it returns - 1.

```js
let names = ["David","Cynthia","Raymond"];
let foundDavidIndex = names.indexOf("David"); // return 0
if (foundDavid){
  console.log("Found David at position" + foundDavidIndex)
}
```

#### Converting Arrays to Strings

**join** - returns a string delimited by a comma

**toString** - returns a string delimited by a comma.

```js
let names = ["David","Cynthia","Raymond"];
let namesStr = names.join();
let namesStr2 = names.toString();
console.log(nameStr); // David, Cynthia, Raymond
```

#### Creating New Arrays from Existing Arrays

**concat** - Allows you to combine 2 or more arrays and returns a new array.

**splice** - Allows you to create a new array from a subset of existing array. Using indices to select the items for the new array.

```js
let students = ["Mike","Clayton","Terrill"];
let students2 = ["Luis","Bob","David"];
let myClass = students.concat(students2);
console.log(myClass); // Mike, Clayton, Terrill, Luis, Bob, David
```

```js
let student = ["Mike","Clayton","Terrill","Luis","Bob","David"];
let topThreeStudents = student.splice(0,3);
console.log(topThreeStudents); // Mike, Clayton, Terrill
```

#### Mutator Functions

#### Adding Elements to an Array

**push** - Adds one or more elements to the end of an array.

**unshift** - Adds one or more elements to the front of the array.

```js
let nums = [1,2,3,4,5];
let newNum = 6;
nums.push(newNum);
console.log(nums) // [1,2,3,4,5,6];
```

```js
let nums = [1,2,3,4,5,6];
let newNum = 0;
nums.unshift(newNum);
console.log(nums) // [0,1,2,3,4,5,6];
```

#### Removing elements from an Array

**pop** - removes an element from the end of the array and returns it

**shift** - removes an element from the front of the array.

```js
let nums = [1,2,3,4,5];
let lastNum = nums.pop();
console.log(lastNum); // 5
```

```js
let nums = [1,2,3,4,5];
let first = nums.shift();
console.log(first); // 1
```



