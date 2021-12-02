## Easy

### Remove Vowels from a String

1. First we need a way to check if a character in a string is a vowel.
2. We also need a temporary variable 
   1. We can create a set that will only contain the vowels.
3. We can use a **for..of** loop to iterate over the string.
   1. Check if the vowel set contains the character we are currently at.
   2. If the character is not found then append it to our result string.
4. Return the result string.

```js
function removeVowels(str) {
  let result = "";
  const vowelMap = new Set();
  vowelMap.add("a");
  vowelMap.add("e");
  vowelMap.add("i");
  vowelMap.add("o");
  vowelMap.add("u");
  for (const s of str) {
    if (vowelMap.has(s)) {
      continue;
    } else {
      result += s;
    }
  }
  return result;
}
```

### Defanging an IP Address

Note: Defanging an IP address, replaces every "." with "[.]"

1. Create a temporary string variable for our return value.
2. Start by iterating over the string using for...of
   1. If the current character in the string is "." then append "[.]" 
   2. If the current character is not "." then append the character.
3. Return the temporary string.

```js
var defangIPaddr = function(address) {
    var answer = "";
    for (const s of address){
        if (s === "."){
            answer += "[.]";
        } else {
            answer += s;
        }
    }
    return answer;
};
```

### Jewels and Stones

1. Start by creating a count variable that will keep track of the count of jewels we have in stones.
2. Create a jewels variable with the type **Set**.
   1. Iterate over each jewel and save the value inside of our **set**.
3. Iterate over the stones argument and if the character is inside the jewels set then increment the counter.
4. Return the count.

```js
var numJewelsInStones = function(jewels, stones) {
    let count = 0;
    const jewelsMap = new Set();
    for (const j of jewels){
        jewelsMap.add(j);
    }
    for (const s of stones){
        if (jewelsMap.has(s)){
            count += 1;
        }
    }
    return count;
};
```

### Shuffle String

1. Start by creating a temporary array for our result.
2. Create a temp array using the spread operator for all the characters in our string.
3. Iterate over the temp array using forEach
   1. Create a temp variable pointing to the corresponding index within **indices[i]**.
   2. Update the temporary array at **indices[i]** with the current character.
4. Return the result array coverted to a string.

```js
var restoreString = function(s, indices) {
    var answer = [];
    const chars = [...s];
    chars.forEach((char,i) => {
        const letterIndex = indices[i];
        answer[letterIndex] = char;
    });
    return answer.join("");
};
```

### Split a String in Balanced **Strings**

```js

```

### To Lower Case

1. Start by setting a temp variable for our result.
2. Iterate over the string using **for...of** 
   1. If the character is equal to the char.toUpperCase() then we have a capital letter.
      1. Append character to the result variable after converting to lower case.
   2. Else
      1. Append the character to the result variable.
3. Return the temp variable.

```js
var toLowerCase = function(s) {
    var temp = "";
    for (const char of s){
        if (char === char.toUpperCase()){
            temp += char.toLowerCase();
        } else {
            temp += char;
        }
    }
    return temp;
};
```

### Unique Morse Code Words

1. Start by creating a set for the unique morse codes.
2. Create a map to look up characters and the morse code value.
3. Iterate over each word in words
   1. Create a temp string to store the morseCode 
   2. Iterate over each character in the current word
      1. Append the morse code value of each character to the **morseCode** variable.
   3. Add the temp string to the unique morse code set.
      1. If the set already has the value then the value wont be added to the set.
   4. Return the size of our unique words set.

```js
var uniqueMorseRepresentations = function(words) {
    const uniqueWords = new Set();
    const charMap = new Map();
    charMap.set("a", ".-");
    charMap.set("b", "-...");
    charMap.set("c", "-.-.");
    charMap.set("d", "-..");
    charMap.set("e", ".");
    charMap.set("f", "..-.");
    charMap.set("g", "--.");
    charMap.set("h", "....");
    charMap.set("i", "..");
    charMap.set("j", ".---");
    charMap.set("k", "-.-");
    charMap.set("l", ".-..");
    charMap.set("m", "--");
    charMap.set("n", "-.");
    charMap.set("o", "---");
    charMap.set("p", ".--.");
    charMap.set("q", "--.-");
    charMap.set("r", ".-.");
    charMap.set("s", "...");
    charMap.set("t", "-");
    charMap.set("u", "..-");
    charMap.set("v", "...-");
    charMap.set("w", ".--");
    charMap.set("x", "-..-");
    charMap.set("y", "-.--");
    charMap.set("z", "--..");

    for (const single_word of words){
        let morseCode = "";        
        for (const char of single_word){            
            morseCode += charMap.get(char);            
        }
        uniqueWords.add(morseCode);
    }
    return uniqueWords.size;
};
```

### Count Substrings with Only One Distinct Letter

```js

```

### Robot Return to Origin

**Note:** This is a grid problem, using x and y coordinates.

1. Create a counter for x and y coordinates

2. Iterate over each character in the string 

   1. If the character is U then increment y

   2. If the character is D then decrement y

   3. If the character is L then decrement x 

   4. If the character is R increment x

3. Return if x and y == 0.


```js
var judgeCircle = function(moves) {
    let x = 0;
    let y = 0;
    for (const move of moves){
        if (move == "U"){
            y--;
        }
        else if (move == "D"){
            y++;
        }
        else if (move == "L"){
            x--;
        }
        else if (move == "R"){
            x++;
        }
    }
    return x == 0 && y == 0;
};
```

### Fizz Buzz

1. Start by creating a temporary array to store the result.

2. Create a starting index with the number 1.

3. Iterate over the array using a while loop or a forloop starting at the index until n.

   1. If the current index is divisible by 15 then push "FizzBuzz" to our temporary array.

   2. If current index is divisible by 3 then push "Fizz"

   3. If current index is divisble by 5 then push "Buzz"

   4. Else push the index.

4. Return the final result.


```js
var fizzBuzz = function(n) {
    let i = 1; 
    let result = [];
    while (i <= n){
        if (i % 3 == 0 && i % 5 == 0){
            result.push("FizzBuzz");
        } else if (i % 3 == 0){
            result.push("Fizz");
        } else if (i % 5 == 0){
            result.push("Buzz");
        } else {
            result.push(String(i));
        }
        i++;
    }
    return result;
};
```

### First Unique Character in a String

1. Start by creating a Map variable to store each character and the frequency.
2. Iterate over string and store the character frequency.
3. Create a temp array for each character in the string (we need this to look up the index later)
4. Iterate over the map and check if the frequency count is 1.
   1. If true then look up the index for the key.
5. Return -1 if for loop doesn't break.

```js
var firstUniqChar = function (s) {
    var charMap = new Map();
    var temp = [...s];
    for (const str of s){
        if (charMap.get(char)){
            charMap.set(char, charMap.get(char) + 1);
        } else {
            charMap.set(char, 1);
        }
    }
    for (const [key,value] of charMap){
        if (value === 1){
            return temp.indexOf(key);
        }
    }
    return -1;
};
```

### Reverse Vowels

1. Start by making a set of vowels to look up.
2. Create an array from the string.
3. Set pointers for i and j
   1. i = 0
   2. j = arr.length - 1
4. Use a while loop to iterate over array.
   1. If both arr[i] and arr[j] are vowels
      1. swap
      2. Increment i
      3. Decrement j
   2. If only arr[i] is a vowel
      1. increment i
   3. If only arr[j] is a vowel
      1. decrement i
5. Return arr as string.

```js
const reverseVowels = (str) => {
  const vowels = new Set();
  vowels.add("a");
  vowels.add("e");
  vowels.add("i");
  vowels.add("o");
  vowels.add("u");
  const strArr = str.split("");
  let i = 0;
  let j = strArr.length - 1;
  while (i < j) {
    if (vowels.has(strArr[i]) && vowels.has(strArr[j])) {
      let temp = strArr[i];
      strArr[i] = strArr[j];
      strArr[j] = temp;
      i++;
      j--;
    }
    if (!vowels.has(strArr[i]) && vowels.has(strArr[j])) {
      i++;
    } else {
      j--;
    }
  }
  return strArr.join("");
};
```

### Valid Anagram

```js
const validAnagram = (str1, str2) => {
  const hashTable = new Map();
  for (const s of str1) {
    if (hashTable.get(s)) {
      hashTable.set(s, hashTable.get(s) + 1);
    } else {
      hashTable.set(s, 1);
    }
  }
  // iterate over the 2nd string and check if hashTable has letter, then decrement
  for (const s of str2) {
    if (hashTable.get(s)) {
      hashTable.set(s, hashTable.get(s) - 1);
    } else {
      return false;
    }
  }
  return true;
};

```

### Valid Palindrome

```js
const validPalindrome = (str) => {
  let hashTable = new Map();
  for (const s of str) {
    if (hashTable.get(s)) {
      hashTable.set(s, hashTable.get(s) + 1);
    } else {
      hashTable.set(s, 1);
    }
  }
  let missingPartner = 0;
  for (const [key, value] of hashTable) {
    if (value == 1) {
      missingPartner += 1;
    }
  }
  return missingPartner > 1;
};
```

### Valid Parentheses

1. Start by creating an tempStack to store the brackets as we come across them.
2. Create a hashLookUp to compare the close brackets to the open ones.
3. As we iterate over the array of brackets. 
   1. If we see an open bracket then push the bracket onto the stack.
   2. If we see a close bracket.
      1. Look at the stack and see the last item on the stack.
         1. The last item on the stack should be a matching open bracket.
         2. If the last item on the stack is a match open bracket then pop off the stack
         3. Else, return false 
4. Return if tempStack.length === 0

```js
var isValid = function (s) {
    var tempStack = [];
    const brackets = new Map();
    brackets.set("]","[");
    brackets.set("}","{");
    brackets.set(")","(");
    for (const b of s){
        if (!brackets.has(b)){
            tempStack.push(b);
        } else if (brackets.has(b) && brackets.get(b) == tempStack[tempStack.length - 1]){
           tempStack.pop();
        } else {
            return false;
        }
    }
    return tempStack.length === 0;
};
```

### Roman to Integer

### Longest Common Prefix

### Excel Sheet Column Number

### Palindrome Permutation

## Medium
