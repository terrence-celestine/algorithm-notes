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

