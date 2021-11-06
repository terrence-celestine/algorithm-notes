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

