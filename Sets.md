#### Overview

- Sets are an unordered collection of related members in which no member occurs more than once.
- **empty set-** a set with no members.
- Two sets are considered equal if they contain exactly the same members.
- A set is considered a subset if all of the members in the first set exist in the second set.

#### Set Operations

- Union - A new set that combines 2 or more sets.
- Intersection - A new set that contains elements found in 2 or more sets.
- Difference - A new set containing members of a set and not found in another set.

```js
function Set() {
    this.dataStore = [];
    this.add = add;
    this.remove = remove;
    this.size = size;
    this.union = union;
    this.intersect = intersect;
    this.subset = subset;
    this.difference = difference;
    this.show = show;
}

function add(data){
    if (this.dataStore.indexOf(data) < 0){
        this.dataStore.push(data);
        return true;
    } else {
        return false;
    }
}

function remove(data){
    let pos = this.dataStore.indexOf(data);
    if (pos > -1){
        this.dataStore.splice(pos,1);
        return true;
    } else {
        return false;
    }
}

function show(){
    return this.dataStore;
}

function contains(data){
    if (this.dataStore.indexOf(data) > -1){
        return true;
    } else {
        return false;
    }
}

function intersect(set){
    let tempSet = new Set();
    for (let i = 0; i < this.dataStore.length; i++){
        if (set.contains(this.dataStore[i])){
            tempSet.add(this.dataStore[i]);
        }
    }
    return tempSet;
}

function subset(set){
    if (this.size() > set.size()){
        return false;
    } else {
        for each (let member in this.dataStore){
            if (!set.contains(member)){
                return false;
            }
        }
    }
    return false;
}

function size(){
    return this.dataStore.length;
}

function difference(set){
    let tempSet = new Set();
    for (let i = 0; i < this.dataStore.length; i++){
        if (!set.contains(this.dataStore[i])){
            tempSet.add(this.dataStore[i]);
        }
    }
    return tempSet;
}
```

#### Excercises

- Modify the Set class so that the class stores its elements in sorted order. Write a
  program to test your implementation.
2. Modify the Set class so that it uses a linked list to store its elements rather than an
array. Write a program to test your implementation.
3. Add the function higher(element) to the Set class. This function returns the least
element in the set strictly greater than the given element. Test your function in a
program.
4. Add the function lower(element) to the Set class. This function returns the greatest
element in the set strictly less than the given element. Test your function in a
program.