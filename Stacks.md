#### Stacks 

A last-in-first-out data structure. The only way to access elements in the stack is from the **top**

```js
var stack = [];
stack.push("1");
stack.push("2");
stack.pop(); // returns 2
```

#### Stack Class

```js
function Stack(){
  this.dataStore = [];
  this.top = 0;
  this.push = push;
  this.pop = pop;
  this.peek = peek;
}
```

Elements are added to the stack using **push**

```js
function push(element){
  this.dataStore[this.top++] = element;
}
```

Elements are removed from the stack using **pop**

```js
function pop(){
  return this.dataStore[--this.top];
}
```

 **peek** - reveals the element at the top of the stack without removing it.

```js
function peek(){
  return this.dataStore[this.top-1];
}
```

**clear** - removes all elements from the stack.

```js
function clear(){
  this.top = 0;
  this.dataStore = [];
}
```

**top** - stores the position of the top item in the stack.

#### Palindromes

A palindrome is a string or number that is the same forwards and backwards.

- racecar
- dad
- 121

A stack can be used to check if a string is a palindrome

```js
function isPalindrome(word){
  let s = [];
  for (let i = 0; i < word.length; i++){
    s.push(word[i]);
  }
  let reverseWord = "";
  while (s.length > 0){
    rword += s.pop();
  }
  if (word == reverseWord){
    return true;
  } else {
    return false;
  }
}

let firstWord = "hello";

if (isPalindrome(firstWord)){
  console.log(firstWord + " is a palindrome");
} else {
  console.log(first Word + "is not a palindrome");
}
```

#### Excercises

1. A stack can be used to ensure that an arithmetic expression has balanced parentheses. Write a function that takes an arithmetic expression as an argument and returns the postion in the expression where a parenthesis is missing. An example of an arithmetic expression with unbalanced parentheses is 2.3 + 23 / 12 + (3.14159 * .24.

2. A postfix expression evaluator works on arithmetic expressions taking the following form:

   *op1 op2 operator*

   Using two stacks—one for the operands and one for the operators—design and implement a JavaScript function that converts infix expressions to postfix expressions, and then use the stacks to evaluate the expression.

3. An example of a real-world stack is a Pez dispenser. Imagine that your virtual Pez dispenser is filled with red, yellow, and white colors and you don’t like the yellow ones. Write a program that uses a stack (and maybe more than one) to remove the yellow ones without changing the order of the other candies in the dispenser.

