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

#### Removing elements from the middle of an Array

**splice** - Takes 3 arguements. A start index, the number of items you want to remove, and items you want to add at the start index.

```js
let nums = [1,2,3,4,5,6,7];
let newNums = [8,9,10];
nums.splice(6,0,newNums); // adds the newNums items at index 6
console.log(nums); // [1,2,3,4,5,6,7,8,9,10]
```

**splice** can also be used to remove elements from an array.

```js
let nums = [1,2,3,100,200,300,400,4,5];
nums.splice(3,4);
console.log(nums); // 1,2,3,4,5
```

#### Putting Array Elements in Order

**reverse** - Reverses the order of the elements of an array.

```js
let nums = [1,2,3,4,5];
nums.reverse();
console.log(nums); // [5,4,3,2,1]
```

**sort** - Sorts the elements of an array in order. 

```js
let nums = [3,1,2,100,4,200];
nums.sort();
console.log(nums); // 1,100,2,200,3,4
```

#### Iterator Functions

#### Non-array-generating functions

**forEach** - takes a function and applies the function to each element of an array.

```js
function square(num){
    console.log(num, num * num);
}
let nums = [1,2,3,4,5,6,7,8,9,10];
nums.forEach(square); // 1 1, 2 4, 3 9, 4 16....
```

**every** - applies a Boolean function to an array and returns true if the function can return true for every element in the array. 

```js
function isEven(num){
    return num % 2 == 0;
}
let nums = [2,4,6,8,10];
let even = nums.every(isEven);
if (even){
    console.log('all numbers are even');
} else {
    console.log('not all numbers are even');
}
// returns "all numbers are even"
```

**some** - applies a Boolean function to an array and returns true if at least one of the elements in the array returns true from the Boolean function.

```js
function isEven(num){
    return num % 2 == 0;
}
let nums = [1,2,3,4,5,6,7];
let someEven = nums.some(isEven);
if (someEven){
    console.log("some numbers are even");
} else {
    console.log("no numbers are even");
}
```

**reduce** - 

**reduceRight**

#### Two-Dimensional and Multidimensional Arrays

Arrays are only one-dimensional, but you can create multidimensional arrays by creating arrays of arrays. 

#### Creating Two-Dimensional Arrays

```js
let twod = [];
let rows = 5;
for (let i = 0; i < rows; i++){
    twod[i] = [];
}
```

We can also create a two-dimesional array and initialize it to a set of values in one line:

```js
let grades = [[89, 77, 78],[76, 82, 81],[91, 94, 89]];
console.log(grades[0,2]); // 78
```

#### Processing Two-Dimensional Arrays

Since each element of the array is another array we need to use 2 for loops to iterate over the nested array's values.

```js
var grades = [[89, 77, 78],[76, 82, 81],[91, 94, 89]];
var total = 0;
var average = 0.0;
for (var row = 0; row < grades.length; ++row) {
    for (var col = 0; col < grades[row].length; ++col) {
        total += grades[row][col];
    }
    average = total / grades[row].length;
    console.log("Student" + parseInt(row+1) + " average:"  + average.toFixed(2)); 
    // Student 1 average: 81.33
    total = 0;
    average = 0.0;
}
```

#### Jagged Arrays

A jagged array is an array where the nested arrays have different number of elements. One nested array might have 3 and the other 5 elements.

```js
var grades = [[89, 77],[76, 82, 81],[91, 94, 89, 99]];
```

#### Arrays of Objects

Arrays can also consist of objects.

```js
function Point(x,y){
    this.x = x;
    this.y = y;
}

let p1 = new Point(1,2);
let p2 = new Point(3,5);
let p3 = new Point(2,8);

let points = [p1,p2,p3];

for (var i = 0; i < points.length; ++i) {
    	console.log("Point " + points[i].x ", " + points[i]
.y;
}
//Point 1: 1, 2
//int 2: 3, 5
//int 3: 2, 8
Point 4: 4, 4
```

#### Exercises

1. Create a grades object that stores a set of student grades in an object. Provide a
   function for adding a grade and a function for displaying the student’s grade average.
2. Store a set of words in an array and display the contents both forward and backward.

```js
let words = ["Hello", "World"];
console.log(words.join(" ")); // Hello World
console.log(words.reverse().join(" ")); // World Hello
```

1. Modify the weeklyTemps object in the chapter so that it stores a month’s worth of
  data using a two-dimensional array. Create functions to display the monthly average,
  a specific week’s average, and all the weeks’ averages.
2. Create an object that stores individual letters in an array and has a function for
  displaying the letters as a single word.
  Exercises

### Lists
