#### Overview

- In many applications the keys are strings. 

````js
function HashTable(){
  this.table = new Array(137);
  this.simpleHash = simpleHash;
  this.showDistro = showDistro;
  this.put = put;
  this.get = get;
}
````

A simple hash function that seems to work is to sum the ASCII values of the key and divide the total by the length of the hash table.

```js
function simpleHash(data){
  let total = 0;
  for (let i = 0; i < data.length; i++){
    total += data.charCodeAt(i);
  }
  return total % this.table.length;
}
```

**put -** adds data to the table.

```js
function put(data){
  let pos = this.simpleHash(data);
  this.table[pos] = data;
}
```

**get - ** prints data to the table

```js
function get(key) {
	return this.table[this.betterHash(key)];
}
```

**showDistro - ** prints the table.

```js
function showDistro() {
  let n = 0;
  for (let i = 0; i < this.table.length; ++i){
    if (this.table[i] != undefined){
      console.log(i + ":" + this.table[i]);
    }
  }
}
```

**betterHash - ** uses Horner's algorithm to create keys that avoid collisions.

```js
function betterHash(string, arr){
  const H = 37;
  let total = 0;
  for (let i = 0; i < string.length; i++){
    total += H * total + string.charCodeAt(i);
  }
  total = total % arr.length;
  return parseInt(total);
}
```

#### Collision resolution

There are 2 ways to resolve collisions when two keys point to the same position in an table.

1. **Separate Chaining - ** After creating our table assign each value of array as another array. That was if 2 or more keys point to the same spot in the table we can simply add the item to the nested array.

```js
function buildChains(){
  for (let i = 0; i < this.table.length; ++i){
    this.table[i] = new Array();
  }
}

function put(key, data) {
		var pos = this.betterHash(key);
    var index = 0;
	if (this.table[pos][index] == undefined) {
			this.table[pos][index+1] = data;
	}
	++index;
	else {
		while (this.table[pos][index] != undefined) {
			++index;
		}
		this.table[pos][index] = data;
	}
}

function get(key) {
var index = 0;
var hash = this.betterHash(key);
if (this.table[pos][index] = key) {
return this.table[pos][index+1];
}
	index += 2;
else {
	while (this.table[pos][index] != key) {
		index += 2;
	}
		return this.table[pos][index+1];
	}
	return undefined;
}

function showDistro(){
    let n = 0;
    for (let i = 0; i < this.table.length; i++){
        if (this.table[i][0] != undefined){
            console.log(i + ":" + this.table[i]);
        }
    }
}
```

1. **Linear Probing**
   1. **put - **  Adding data to the table if there is a collision, look for the next available element and insert the data there.
   2. **get - ** Starts searching the hash table at the hashed position. If the hashed key matches the key passed then return the values at the hash.

```js
// linear probing put/get
function put(key,data){
  let pos = this.betterHash(key);
  if (this.table[pos] == undefined){
    this.table[pos] = key;
    this.values[pos] = data;
  } else {
    while (this.table[pos] != undefined){
      pos++;
    }
    this.table[pos] = key;
    this.values[pos] = data;
  }
}

function get(key){
    let hash = -1;
    hash = this.betterHash(key);
    if (hash > -1){
        for (let i = hash; this.table[hash] != undefined; i++){
            if (this.table[hash] == key){
                return this.values[hash];
            }
        }
    }
    return undefined;
}
```

### Exercises

1. Use linear probing to create a simple dictionary to store the definitions of words. Your program should have two parts. The first part reads a text file that contains a list of words and definitions and stores them in a hash table. The second part of the program allows a user to enter a word and see the definition of that word.

```js

function HashTable() {
  this.table = new Array(137);
  this.values = new Array(137);
  this.betterHash = betterHash;
  this.put = put;
  this.get = get;
  function betterHash(string, arr) {
    const H = 37;
    let total = 0;
    for (let i = 0; i < string.length; i++) {
      total += H * total + string.charCodeAt(i);
    }
    total = total % this.table.length;
    return parseInt(total);
  }
  // linear probing put/get
  function put(key, data) {
    let pos = this.betterHash(key);
    if (this.table[pos] == undefined) {
      this.table[pos] = key;
      this.values[pos] = data;
    } else {
      while (this.table[pos] != undefined) {
        pos++;
      }
      this.table[pos] = key;
      this.values[pos] = data;
    }
  }
  function get(key) {
    let hash = -1;
    hash = this.betterHash(key);
    if (hash > -1) {
      for (let i = hash; this.table[hash] != undefined; i++) {
        if (this.table[hash] == key) {
          return this.values[hash];
        }
      }
    }
    return undefined;
  }
}

const definitions = [
  {
    name: "apple",
    definition:
      "the usually round, red or yellow, edible fruit of a small tree, Malus sylvestris, of the rose family.",
  },
];

const hTable = new HashTable();

definitions.forEach((item) => {
  hTable.put(item.name, item.definition);
});

// iterate over defitions and add to dictionary
console.log(hTable.get("apple"));
```

1. Repeat exercise 1 using separate chaining.

```js
function HashTable() {
  this.table = new Array(137);
  this.betterHash = betterHash;
  this.put = put;
  this.get = get;
  this.showDistro = showDistro;
  this.buildChains = buildChains;
  function betterHash(string, arr) {
    const H = 37;
    let total = 0;
    for (let i = 0; i < string.length; i++) {
      total += H * total + string.charCodeAt(i);
    }
    total = total % this.table.length;
    return parseInt(total);
  }
  function buildChains() {
    for (let i = 0; i < this.table.length; ++i) {
      this.table[i] = new Array();
    }
  }
  function put(key, data) {
    var pos = this.betterHash(key);
    var index = 0;
    if (this.table[pos][index] == undefined) {
      this.table[pos][index + 1] = data;
    } else {
      ++index;
      while (this.table[pos][index] != undefined) {
        ++index;
      }
      this.table[pos][index] = data;
    }
  }
  function get(key) {
    var index = 0;
    var pos = this.betterHash(key);
    if ((this.table[pos][index] = key)) {
      return this.table[pos][index + 1];
    } else {
      index += 2;
      while (this.table[pos][index] != key) {
        index += 2;
      }
      return this.table[pos][index + 1];
    }
    return undefined;
  }
  function showDistro() {
    for (let i = 0; i < this.table.length; i++) {
      if (this.table[i][0] != undefined) {
        return i + ":" + this.table[i];
      }
    }
  }
}
```

1. Write a program using hashing that reads a text file and compiles a list of the words in the file with the number of times each word appears in the file.

```js
function HashTable() {
  this.table = new Array(137);
  this.values = new Array(137);
  this.betterHash = betterHash;
  this.put = put;
  this.get = get;
  function betterHash(string) {
    const H = 37;
    let total = 0;
    for (let i = 0; i < string.length; i++) {
      total += H * total + string.charCodeAt(i);
    }
    total = total % this.table.length;
    return parseInt(total);
  }
  // linear probing put/get
  function put(key) {
    let pos = this.betterHash(key);
    if (this.table[pos] == undefined) {
      this.table[pos] = key;
      this.values[pos] = 1;
    } else {
      this.values[pos] = this.values[pos] + 1;
    }
    console.log(this.table[pos] + ":" + this.values[pos]);
  }
  function get(key) {
    let hash = -1;
    hash = this.betterHash(key);
    if (hash > -1) {
      for (let i = hash; this.table[hash] != undefined; i++) {
        if (this.table[hash] == key) {
          return this.values[hash];
        }
      }
    }
    return undefined;
  }
}

const sentence =
  "the usually round, red or yellow, edible fruit of a small tree, Malus sylvestris, of the rose family.";

const hTable = new HashTable();

const words = sentence.split(" ");

words.forEach((word) => {
  word = word.replace(",", "");
  word = word.replace(".", "");
  hTable.put(word);
});
```

