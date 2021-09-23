A queue is a first in first out data structure. Queues can be made using an array.

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

