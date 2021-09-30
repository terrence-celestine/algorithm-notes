### Excercises

1. Write a program that takes a set of names and phone numbers from a text file and
  stores them in a Dictionary object. Include in your program the ability to display
  one phone number, display all phone numbers, add new phone numbers, remove
  phone numbers, and clear out the list of numbers.

```js
function phoneBook(items) {
  this.data = new Map();
  this.lookUp = lookUp;
  this.showAll = showAll;
  this.addNumber = addNumber;
  this.removeNumber = removeNumber;
  this.clearPhoneBook = clearPhoneBook;

  let temp = new Map();
  const seperateNumbers = items.split(",");
  seperateNumbers.forEach(function (item) {
    const name = item.split(" ")[0];
    const number = item.split(" ")[1];
    temp.set(name, number);
  });

  this.data = temp;

  function lookUp(name) {
    if (this.data.has(name)) {
      return "Found " + name + " " + this.data.get(name);
    }
    return undefined;
  }

  function addNumber(name, number) {
    if (name.length === 0 || number.length === 0) {
      return false;
    }
    if (this.data.has(name)) {
      return false;
    }
    this.data.set(name, number);
    return true;
  }

  function showAll() {
    for (const [k, v] of this.data) {
      console.log(k, v);
    }
    return true;
  }

  function removeNumber(name) {
    if (!this.data.has(name)) {
      return undefined;
    }
    this.data.delete(name);
    return true;
  }

  function clearPhoneBook() {
    this.data = new Map();
    return true;
  }
}
```



1. Using the Dictionary class, write a program that stores the number of occurrences
  of words in a text. Your program should display each word in a text just once as
  well as the number of times the word occurs in the text. For example, given the text
  “the brown fox jumped over the blue fox,” the output will be:

the: 2
brown: 1
fox: 2
jumped: 1
over: 1
blue: 1

```js
const wordCounter = (sentence) => {
  const countMap = new Map();
  const words = sentence.split(" ");
  words.forEach((word) => {
    if (countMap.get(word)) {
      countMap.set(word, countMap.get(word) + 1);
    } else {
      countMap.set(word, 1);
    }
  });
  for (const [k, v] of countMap) {
    console.log(k + ":" + v);
  }
};
```

3. Rewrite exercise 2 so that it displays the words in sorted order.  

