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

```js
function grades() {
  this.data = [];
  this.addGrade = addGrade;
  this.average = average;
}

function addGrade(grade) {
  this.data.push(grade);
}

function average() {
  let total = 0;
  let grades = this.data;
  grades.forEach(function (g) {
    total += g;
  });
  return (total / this.data.length).toFixed(2);
}

let student = new grades();
student.addGrade(80);
student.addGrade(65);
student.addGrade(49);

console.log(student.average());
```

2. Store a set of words in an array and display the contents both forward and backward.

```js
let words = ["Hello", "World"];
console.log(words.join(" ")); // Hello World
console.log(words.reverse().join(" ")); // World Hello
```

3. Modify the weeklyTemps object in the chapter so that it stores a month’s worth of
   data using a two-dimensional array. Create functions to display the monthly average,
     a specific week’s average, and all the weeks’ averages.

4. Create an object that stores individual letters in an array and has a function for
   displaying the letters as a single word.

```js

function makeWord() {
  this.data = [];
  this.addLetter = addLetter;
  this.combineLetters = combineLetters;
}

function addLetter(letter) {
  this.data.push(letter);
}

function combineLetters() {
  return this.data.join("");
}

var newWord = new makeWord();
newWord.addLetter("h");
newWord.addLetter("e");
newWord.addLetter("l");
newWord.addLetter("l");
newWord.addLetter("o");
console.log(newWord.combineLetters());
```

### Lists

```js
function List(){
    this.listSize = 0;
    this.pos = 0;
    this.dataStore = [];
    this.clear = clear;
    this.find = find;
    this.toString = toString;
    this.insert = insert;
    this.append = append;
    this.remove = remove;
    this.front = front;
    this.end = end;
    this.prev = prev;
    this.next = next;
    this.length = length;
    this.currPos = currPos;
    this.moveTo = moveTo;
    this.getElement = getElement;
    this.length = length;
    this.contains = contains;
}
```

#### Adding an Element to a List

Adds a new element onto the list at the next available position, by incrementing the listSize variable.

```js
function append(element){
    this.dataStore[this.listSize++] = element;
}
```

#### Finding an element

Takes an element and iterates through the array, if the element in the array matches the one passed to our function then returns the index. If no match is found then returns -1.

```js
function find(element){
    for (let i = 0; i < this.dataStore.length; i++){
        if (this.dataStore[i] == element){
            return i;
        }
    }
    return -1;
}
```

#### Removing an Element from a List

Uses the position returned by **find** to modify the dataStore array. After modifying the array then listSize is decremented by 1. The function returns true if an element is removed, and false otherwise.

```js
function remove(element){
    let foundAt = this.find(element);
    if (foundAt > -1){
        this.dataStore.splice(foundAt,1);
        --this.listSize;
        return true;
    } 
    return false;
}
```

#### Length: Determine the number of elements in a List

Returns the number of elements in a list

```js
function length(){
    return this.listSize;
}
```

#### toString: Retrieving a List's Elements

Returns the elements array

```js
function toString(){
    return this.dataStore;
}
```

#### Insert: Inserting an Element into a List

```js
function insert(element, after){
    let insertPos = this.find(after);
    if (insertPos > -1){
        this.dataStore.splice(insertPos,0,element);
        ++this.listSize;
        return true;
    }
    return false;
}
```

#### Clear: Removing All Elements from a List

Uses teh delete operate to delete the dataStore array and re-assigns the dataStore property to a new array. Sets the values of listSize and pos to 0 to restart the list.

```js
function clear(){
    delete this.dataStore;
    this.dataStore = [];
    this.listSize = 0;
    this.pos = 0;
}
```

#### Contains: Determines if a given value is in a List

```js
function contains(element){
    for (let i = 0; i < this.dataStore.length; i++){
        if (this.dataStore[i] == element){
            return true;
        }
    }
    return false;
}
```

#### Traversing a List

#### Front

Updates the current position to the first index

```js
function front(){
    this.pos = 0;
}
```

#### End

Updates the current position to the last index.

```js
function end(){
    this.pos = this.listSize-;
}
```

#### Prev

If the position is greater than 0 then moves the current position to the previous element position.

```js
function prev(){
    if(this.pos > 0){
        --this.pos;
    }
}
```

#### Next

If the current position is less than the last index then increment current position.

```js
function next(){
    if (this.pos < this.listSize-1)
        ++this.pos;
}
```

#### currPos

Returns the current position

```js
function currPos(){
    return this.pos;
}
```

#### moveTo

Updates the current position with an index passed to it.

```js
function moveTo(position){
    this.pos = position;
}
```

#### getElement

Returns the element at current position

```js
function getElement(){
    return this.dataStore[this.pos];
}
```

#### Iterating Through a List

#### Kiosk Program

#### Excercises

1. Write a function that inserts an element into a list only if the element to be inserted
  is larger than any of the elements currently in the list. Larger can mean either greater
  than when working with numeric values, or further down in the alphabet, when
  working with textual values.

```js
let numbers = [1, 2, 3, 4, 5];

function addOnlyLarger(element) {
  let largestElementInList = Math.max(...numbers);
  if (element > largestElementInList) {
      numbers.push(element);
      return true;
  }
  return false;
}
```

1. Write a function that inserts an element into a list only if the element to be inserted
  is smaller than any of the elements currently in the list.

```js
let numbers = [1, 2, 3, 4, 5];

function addOnlyLarger(element) {
  let largestElementInList = Math.min(...numbers, element);
  if (element === largestElementInList) {
      numbers.push(element);
      return true;
  }
  return false;
}
```

1. Create a Person class that stores a person’s name and their gender. Create a list of
  at least 10 Person objects. Write a function that displays all the people in the list of
  the same gender.

```js
function Person(name, gender) {
  this.name = name;
  this.gender = gender;
}

let personList = [];
let p1 = new Person("A", "male");
let p2 = new Person("B", "female");
let p3 = new Person("C", "male");
let p4 = new Person("D", "female");

personList.push(p1, p2, p3, p4);

function getPersonByGender(gender) {
  return personList.filter(function (p) {
    return p["gender"] == gender;
  });
}

console.log(getPersonByGender("male"));

```

1. Modify the video-rental kiosk program so that when a movie is checked out it is
  added to a list of rented movies. Display this list whenever a customer checks out
  a movie.
2. Create a check-in function for the video-rental kiosk program so that a returned
  movies is deleted from the rented movies list and is added back to the available
  movies list.

### Stacks

