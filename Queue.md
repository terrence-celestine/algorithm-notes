#### Queue

A queue is a first in first out data structure. 

#### Using an array

**push** - adds an element to the back of the queue.

**shift** - adds an element to the front of the queue.

```js
var myQueue = [];
myQueue.push('a');
myQueue.push('b');
myQueue.shift(); // removes a
myQueue.shift(); // removes b
```

Defining a Queue class

```js
function Queue(){
  this.dataStore = [];
  this.enqueue = enqueue;
  this.dequeue = dequeue;
  this.front = front;
  this.back = back;
  this.toString = toString;
  this.empty = empty;
}
```

**enqueue** - adds element at the end of the queue.

```js
function enqueue(element){
  this.dataStore.push(element);
}
```

**dequeue** - removes an element from the front of the queue.

```js
function dequeue(){
  this.dataStore.shift();
}
```

**front** - returns the element at the first index.

```js
function front(){
  return this.dataStore[0];
}
```

**back** - returns the element at the end of the queue.

```js
function back(){
  return this.dataStore[this.dataStore.length - 1];
}
```

**toString** - returns all the elements in the queue as a string.

```js
function toString(){
  let retStr = '';
  for (let i = 0; i < this.dataStore.length; i++){
    retStr += this.dataStore[i] + "\n";
  }
  return retStr;
}
```

**empty** - returns if the queue is empty

```js
function empty(){
  if (this.dataStore.length == 0){
    return true;
  } else {
    return false;
  }
}
```

Queue Class

```js
function Queue() {
  this.dataStore = [];
  this.enqueue = enqueue;
  this.dequeue = dequeue;
  this.front = front;
  this.back = back;
  this.toString = toString;
  this.empty = empty;
}

function enqueue(element) {
  this.dataStore.push(element);
}

function dequeue() {
  return this.dataStore.shift();
}

function front() {
  return this.dataStore[0];
}

function back() {
  return this.dataStore[this.dataStore.length - 1];
}

function toString() {
  var retStr = "";
  for (var i = 0; i < this.dataStore.length; ++i) {
    retStr += this.dataStore[i] + "\n";
  }
  return retStr;
}

function empty() {
  if (this.dataStore.length == 0) {
    return true;
  } else {
    return false;
  }
}
```

#### Priority Queue 

```js
function Patient(name, code){
    this.name = name;
    this.code = code;
}
```

In a priority queue elements are removed in a FIFO order based on their priority code. The lower the code the higher priority.

```js
function dequeue(){
    let priority = this.dataStore[0].code;
    for (let i = 1; i < this.dataStore.length; i++){
        let curr = this.dataStore[i].code;
        if (curr['code'] < priority){
            priority = i;
        }
    }
    return this.dataStore.splice(priority,1);
}
```

#### Exercises

1. Modify the Queue class to create a Deque class. A deque is a queue-like structure
   that allows elements to be added and removed from both the front and the back of
   the list. Test your class in a program.
2. Use the Deque class you created in Example 5-1 to determine if a given word is a
   palindrome.
3. Modify the priority queue example from Example 5-5 so that the higher-priority
   elements have higher numbers rather than lower numbers. Test your implementation
   with the example in the chapter.
4. Modify the ED example (Example 5-5) so the user can control the activity in the
   ED. Create a menu system that allows the user to choose from the following activities:
   a. Patient enters ED.
   b. Patient is seen by doctor.
   c. Display list of patients waiting to be seen.
