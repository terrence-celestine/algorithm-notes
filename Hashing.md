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

1. **Seperate Chaining - ** After creating our table assign each value of array as another array. That was if 2 or more keys point to the same spot in the table we can simply add the item to the nested array.
2. **Linear Probing -** When adding data to the table if there is a collision, look for the next available element and insert the data there.

```js
function buildChains(){
  for (let i = 0; i < this.table.length; ++i){
    this.table[i] = new Array();
  }
}

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
```

### Excercises

1. Use linear probing to create a simple dictionary to store the definitions of words. Your program should have two parts. The first part reads a text file that contains a list of words and definitions and stores them in a hash table. The second part of the program allows a user to enter a word and see the definition of that word.
2. Repeat exercise 1 using separate chaining.
3. Write a program using hashing that reads a text file and compiles a list of the words in the file with the number of times each word appears in the file.
