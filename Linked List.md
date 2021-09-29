**head** - the beginning of the linked list.

**tail** - the end of the linked list.

An item inside of a Linked List is called a Node.

#### The Node Class

A node consists of two properties.

**element -** which stores the node's data.

**next -** which points to the next node in the list.

```js
function Node(element){
    this.element = element;
    this.next = null;
}
```

#### The Linked List Class

Our Linked List class includes functions for inserting new nodes, removing nodes, and finding a particular data value in a list.

```js
function LList(){
    this.head = new Node("head");
    this.find = find;
    this.insert = insert;
    this.remove = remove;
    this.display = display;
}


```

#### Inserting New Nodes

To insert a new node, you have to specify which node you want to insert before or after. In order to find the node we want to insert at we need to define a helper function called **find()**. 

```js
function find(item){
    let currNode = this.head;
    while (currNode.element != item){
        currNode = currNode.next;
    }
    return currNode;
}
```

```js
function insert(newElement, item){
    let newNode = new Node(newElement);
    let current = this.find(item);
    newNode.next = current.next;
    current.next = newNode;
}
```

#### Removing Previous Node

```js
function findPrevious(item){
    let currNode = this.head;
    while (!(currNod.next == null) && (currNode.next.element != item)) {
        currNode = currNode.next;
    }
    return currNode;
}
```

```js
function remove(item){
    let prevNode = this.findPrevious(item);
    if (!(prevNode.next == null)) {
        prevNode.next = prevNode.next.next;
    }
}
```

#### Double Linked List

```js
function Node(element){
    this.element = element;
    this.next = null;
    this.previous = null;
}

function DLList(){
    this.head = new Node("head");
    this.find = find;
    this.findLast = findLast;
    this.insert = insert;
    this.remove = remove;
    this.displayReverse = displayReverse;
}

function find(item){
    let currNode = this.head;
    while (!(currNode.element != item)){
        currNode = currNode.next;
    }
    return currNode;
}

function findLast(){
    let currNode = this.head;
    while (!(currNode.next == null)){
        currNode = currNode.next;
    }
    return currNode;
}

function insert(newElement, item){
    let newNode = new Node(newElement);
    let current = this.find(item);
    newNode.next = current.next;
    newNode.previous = current.previous;
    current.next = newNode;
}

function remove(item){
    let currNode = this.find(item);
    if (!(currNode.next == null)){
        currNode.previous.next = currNode.next;
        currNode.next.previous = currNod.previous;
        currNode.next = null;
        currNode.previous = null;
    }
}

function displayReverse(){
    let currNode = this.head;
    currNode = this.findLast();
    while (!(currNode.previous == null)) {
        console.log(currNode.element);
        currNode = currNode.previous;
    }
}
```

#### Excercises

- Implement the advance(n) function so that when executed, the current node is
  moved n nodes forward in the list.
- Implement the back(n) function so that when executed, the current node is moved
  n spaces backward in the list.
- Implement the show() function, which displays the data associated with the current
  node.
- Write a program that uses a singly linked list to keep track of a set of test grades
  entered interactively into the program.
- Rewrite your solution to Example 6-4 using a doubly linked list.
- According to legend, the first-century Jewish historian Flavius Josephus was about
  to be captured along with a band of 40 compatriots by Roman soldiers during the
  Jewish-Roman War. The Jewish soldiers decided that they preferred suicide to being
  captured and devised a plan for their demise. They were to form a circle and kill
  every third soldier until they were all dead. Josephus and one other decided they
  wanted no part of this and quickly calculated where they needed to place themselves
  so they would be the last survivors. Write a program that allows you to place n
  people in a circle and specify that every mth person will be killed. The program
  should determine the number of the last two people left in the circle. Use a circularly
  linked list to solve the problem.