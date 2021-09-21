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

