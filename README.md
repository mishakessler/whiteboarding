# Whiteboarding for JavaScript-React Engineers <!-- omit in toc -->

Questions are organized by category (technical versus behavioral) and type (whiteboarding challenges, knowledge checks, etc.) Each question is given with the relevant answers– for whiteboarding challenges, this includes Starter Code, Questions (for the interviewer), Pseudocode, Brute-Force Solutions, and finally, the Refactored Solutions, where possible; for knowledge checks, this includes Key Talking Points and Conversational Examples, where possible.

***

## Table of Contents <!-- omit in toc -->

- [Whiteboarding Process](#whiteboarding-process)
- [Whiteboarding Challenges](#whiteboarding-challenges)
  - [Anagrams](#anagrams)
  - [Change To Anagram](#change-to-anagram)
  - [Markdown to HTML](#markdown-to-html)
  - [Hungry Bunny](#hungry-bunny)
  - [Palindrome](#palindrome)
  - [Date Palindrome](#date-palindrome)

***

## Whiteboarding Process

The solutions provided for these challenges attempt to reflect the optimal flow of a technical interview:

1. **Start by gaining as much information as possible; ask questions of the interviewer.** _(This may give you insights into solutions or awareness of edge cases that need to be accounted for, which you would've missed otherwise.)_
2. **Proceed with explaining how you think it should be solved, then, when you're comfortable, pseudocode the problem.** _(This gives you insight into your assumptions and helps you think through the entire problem, as well as giving you a chance to see the interviewers' subtle reactions to your ideas.)_
3. **If it hasn't already been discussed, ask if it would be okay to solve the challenge in your preferred language.** _(They'll almost always say, "Of course," but it's nice for context and interviewing purposes.)_
4. **If you need to, start by "brute-forcing" the problem.** _(This refers to solving the challenge with highly inefficient or non-DRY code. It's best to acknowledge that you recognize the problems with such a brute-force solution, but that you would like to think through the problem in an easier form first.)_
5. **Once you've solved the challenge with a brute-force solution, discuss the limitations and inefficiencies of your solution.** _(For example, how you would improve the code in general? What form must the function's arguments take for your solution to work? What edge-cases will this solution not account for? What is the Big O complexity? How could you improve the efficiency?)_
6. **Test your code! Confirm everything is happening as you expected. Find any edge cases and discuss.** _(This is going above and beyond in the eyes of an interviewer; an appreciation for the importance of TDD is vital in the real world.)_
7. **Ask if the interviewer would like to see a refactored, more efficient solution.** _(Even if you can't think of any ways, ask! It's good to acknowledge that there are better solutions, spend a minute thinking on it, and if nothing comes to mind, or you're worried about syntax and convention, say so.)_

## Whiteboarding Challenges

### Anagrams

<details><summary>Expand</summary>

> Determine if two strings are anagrams.

<details style="margin-left: 50px"><summary>Starter Code</summary>

```js
const anagram = () => {

}
```

</details>

<details style="margin-left: 50px"><summary>Clarifying Questions</summary>

- Are the strings both always lowercase?
- Are the strings always going to be the same length?
- Will the two strings always by single words, or can there be multiple words?
- Will spaces matter in the determination of the anagram?
  - i.e., could 'hillary' be an anagram for 'yar hill'?

</details>

<details style="margin-left: 50px"><summary>Pseudocode</summary>

- So I am going to take the two strings you give me as arguments, and I want to return true if the two are anagrams and false if they are not.
- In order to do this, I need to check if each character used in the first string is used the same number of times in the second string.
- If spaces do not matter, I need to simply remove any spaces found in either of the original strings.
- I will need to use a.....(loop, sorting algorithm, etc.) to do...... so that .......

</details>

<details style="margin-left: 50px"><summary>Brute Force Solution</summary>

```javascript

const anagram = (str1, str2) => {
  if (str1 === str2) {
    return true;
  }
  let counts = {};
  for (let i = 0; i < str1.length; i++) {
    let index = str1.charCodeAt(i) - 97;
    counts[index] = (counts[index] || 0) + 1;
  }
  for (let j = 0; j < str2.length; j++) {
    let index = str2.charCodeAt(j) - 97;
    if (!counts[index]) {
      return false;
    }
    counts[index]--;
  }
  return true;
}
```

</details>

<details style="margin-left: 50px"><summary>Testing</summary>

```javascript
console.log(anagram("mary", "army"));
console.log(anagram("the litttttle one", "the litttle one"));

console.log(refactoredAnagram("mary", "army"));
console.log(refactoredAnagram("the litttttle one", "the litttle one"));
```

</details>

<details style="margin-left: 50px"><summary>Refactored Solution</summary>

```javascript
const refactoredAnagram = (string1, string2) => {
  return
    str1
      .toLowerCase()
      .split("")
      .sort()
      .join("") ===
    str2
      .toLowerCase()
      .split("")
      .sort()
      .join("")
    ? true
    : false;
}

```

</details>

<details style="margin-left: 50px"><summary>Variations</summary>

[Change To Anagram](#Change-To-Anagram)

</details>
</details>

### Change To Anagram

<details><summary>Expand</summary>

> Return the minimum amount of letters which need to be removed in order to make two strings an anagram.

<details style="margin-left: 50px"><summary>Refactored Solution</summary>

```javascript
const changeToAnagram = () => {
  if (a === b) {
    return true;
  }

  let str1 = a
    .toLowerCase()
    .split("")
    .sort()
    .join("");
  let str2 = b
    .toLowerCase()
    .split("")
    .sort()
    .join("");
  let removed = 0;

  let counts = {};
  for (let i = 0; i < str1.length; i++) {
    let index = str1.charCodeAt(i) - 97;
    counts[index] = (counts[index] || 0) + 1;
  }
  console.log(counts);
  for (let j = 0; j < str2.length; j++) {
    let index = str2.charCodeAt(j) - 97;
    if (!counts[index]) {
      removed = removed + 1;
      console.log(index, " does not exist", removed);
    }
    if (counts[index]) {
      counts[index]--;
    }
  }
  console.log(counts);
  let reserved = [];
  reserved = Object.values(counts);
  let added = reserved.reduce((a, b) => a + b, 0);
  console.log(added);
  removed = removed + added;
  return removed;
}
```

</details>
</details>

### Markdown to HTML

<details><summary>Expand</summary>

> Convert markdown text to HTML.

<details style="margin-left: 50px"><summary>Starter Code</summary>

```js
const convertToHTML = () => {

}
```

</details>

<details style="margin-left: 50px"><summary>Clarifying Questions</summary>

- Are the strings both always lowercase?
- Are the strings always going to be the same length?
- Will the two strings always by single words, or can there be multiple words?
- Will spaces matter in the determination of the anagram?
  - i.e., could 'hillary' be an anagram for 'yar hill'?

</details>

<details style="margin-left: 50px"><summary>Pseudocode</summary>

- So I am going to take the two strings you give me as arguments, and I want to return true if the two are anagrams and false if they are not.
- In order to do this, I need to check if each character used in the first string is used the same number of times in the second string.
- If spaces do not matter, I need to simply remove any spaces found in either of the original strings.
- I will need to use a.....(loop, sorting algorithm, etc.) to do...... so that .......

</details>

<details style="margin-left: 50px"><summary>Brute Force Solution</summary>

```javascript

const anagram = (str1, str2) => {
  if (str1 === str2) {
    return true;
  }
  let counts = {};
  for (let i = 0; i < str1.length; i++) {
    let index = str1.charCodeAt(i) - 97;
    counts[index] = (counts[index] || 0) + 1;
  }
  for (let j = 0; j < str2.length; j++) {
    let index = str2.charCodeAt(j) - 97;
    if (!counts[index]) {
      return false;
    }
    counts[index]--;
  }
  return true;
}
```

</details>

<details style="margin-left: 50px"><summary>Testing</summary>

```javascript
console.log(anagram("mary", "army"));
console.log(anagram("the litttttle one", "the litttle one"));

console.log(refactoredAnagram("mary", "army"));
console.log(refactoredAnagram("the litttttle one", "the litttle one"));
```

</details>

<details style="margin-left: 50px"><summary>Refactored Solution</summary>

```javascript
const refactoredAnagram = (string1, string2) => {
  return
    str1
      .toLowerCase()
      .split("")
      .sort()
      .join("") ===
    str2
      .toLowerCase()
      .split("")
      .sort()
      .join("")
    ? true
    : false;
}

```

</details>

<details style="margin-left: 50px"><summary>Variations</summary>

[Change To Anagram](#Change-To-Anagram)

</details>
</details>

### Hungry Bunny

<details><summary>Expand</summary>

> A very hungry bunny gets into your garden, which is represented by a rectangular, 2D array matrix. For example:
>
> ```
> [
>  [5, 7, 8, 6, 3],
>  [0, 0, 7, 0, 4],
>  [4, 6, 3, 4, 9],
>  [3, 1, 0, 5, 8],
>  [2, 5, 1, 0, 2]
> ]
> ```
>
> The bunny begins to eat the most amount of carrots it can! Calculate how many carrots the bunny will eat if it starts at the center plot and moves up, down, left, or right, only choosing the plot that has the **most** carrots. If there are no carrots left on any adjacent squares, the rabbit will go to sleep.
> Given the above input, your function should return `30` by starting at `3` then moving to `7`, `8`, `7`, `5`.

<details style="margin-left: 50px">

  <summary>Starter Code</summary>

  ```js
  goBunnyGo = (garden, x, y) => {

  }
  ```

</details>

<details style="margin-left: 50px">

  <summary>Clarifying Questions</summary>

- Will the garden always have an exact center plot? If not, which plot is the first?
- Will the bunny ever need to choose between two plots with an identical number of carrots?

</details>

<details style="margin-left: 50px">

  <summary>Pseudocode</summary>

- So I'm going to get an array of arrays that I'm given as an argument, and to start, I'll need to find the middle integer, given the 2D matrix that those arrays create, and initialize a carrot counter as that integer.
- Then, I'll need to compare the adjacent squares, excluding diagonally-adjacent squares, to determine which has the highest integer. I'll add that integer to the carrot counter and repeat.
- When the index reaches a square with no adjacent non-zero integers, I have to return to the total number of carrots, tracked by my counter.
- I'll want to prevent the bunny from going over the same plots multiple times, which means I'll not just have to add to the carrot counter, but I'll want to replace the plot's integer with a 0 when it is eaten.
- I'll also want to prevent the bunny from moving into non-existent plots, which means I need to prevent the bunny from moving into a plot with an index greater than the array lengths.

</details>

<details style="margin-left: 50px">

  <summary>Brute Force Code</summary>

</details>

<details style="margin-left: 50px">

  <summary>Refactored Code</summary>

```js
const goBunnyGo = (garden, x, y) => {
  let carrotCount = garden[x][y];
  garden[x][y] = 0
  let sleepyRabbit = false
  do {
    let right = -1
    let left = -1
    let up = -1
    let down = -1
    if ((garden[x+1])!== undefined){
      right = garden[x+1][y]
    }
    if ((garden[x-1])!== undefined){
      left = garden[x-1][y]
    }
    if ((garden[x][y-1])!== undefined){
      up = garden[x][y-1]
    }
    if ((garden[x][y+1])!== undefined){
      down = garden[x][y+1]
    }
      if (right > left && right > up && right> down){
      carrotCount += right
      right = 0
      x++
      garden[x][y] =0
      }
      else if (left > right && left  > up && left > down){
      carrotCount += left 
      x--
      garden[x][y] =0
      }
      else if (up > left && up > right && up> down){
      carrotCount += up
      y--
      garden[x][y] =0
      }
      else if (down > left && down > up && down> right){
        console.log('down', down)
      carrotCount += down
      y++
      garden[x][y] =0
      }
      else {
        return carrotCount
      }
  } while (!sleepyRabbit)
  return carrotCount
}

const findCenter = (garden) => {
  const length = garden.length;
  const depth = garden[0].length;
  if (length%2 === 1 && depth%2 === 1) {
    const x = Math.floor(length / 2);
    const y = Math.floor(depth / 2);
  } else {
    let x = length/2
    let y = depth /2
  }
    let midArray = []
    let center = garden[x][y]
    let left = -1
    let up = -1
    let diag = -1
    if ((garden[x-1])!== undefined){
      left = garden[x-1][y]
    }
    if ((garden[x][y-1])!== undefined){
      up = garden[x][y-1]
    }
    if ((garden[x-1][y-1])!== undefined){
      diag = garden[x-1][y-1]
    }
      console.log('garden', garden)
      console.log('up', up)
      console.log('left', left)
    console.log('diag', diag)
      if (center > up &&center > left && center > diag ) {
        midArray.push(x)
        midArray.push(y)
        console.log('midArray', midArray)
        return midArray
      }
     else if (left > up  && left > diag){
      midArray.push(x-1)
      midArray.push(y)
      console.log('midArray', midArray)
      return midArray
      }
      else if (up > left && up > diag){
       midArray.push(x)
      midArray.push(y-1)
      console.log('midArray', midArray)
      return midArray
      }
      else if (diag > left && diag > up){
         midArray.push(x-1)
      midArray.push(y-1)
      console.log('midArray', midArray)
      return midArray
      }
    }
  }

const garden = [
  [1, 2, 4, 3],
  [6, 3, 8, 1],
  [3, 15, 6, 2],
  [4, 7, 8, 1]
];

const coord = findCenter(garden)
goBunnyGo(garden, coord[0], coord[1])

```

</details>

<details style="margin-left: 50px">

  <summary>Testing</summary>

</details>
</details>

### Palindrome

<details><summary>Expand</summary>

> Determine if a string is a Palindrome.
> _(A palindrome is a word or sentence that’s spelled the same way both forward and backward, ignoring punctuation, case, and spacing.)_

<details style="margin-left: 50px">

  <summary>Starter Code</summary>

  ```js
  function isPalindrome(string) = {

  }
  ```

</details>

<details style="margin-left: 50px">

  <summary>Clarifying Questions</summary>

- The starter code gives a function declaration; can I convert it to an arrow function?
- Are the strings always single words?
- Will the strings have upper and lowercase letters, spaces, symbols, or punctuation?

</details>

<details style="margin-left: 50px">

  <summary>Pseudocode</summary>

- So I know that I'll have to take a single string and return true if the string is a palindrome, or false if not.
- In order to do this, I need to account for variations and edge case in the string's characters, such as spaces, capitalization, numbers, and symbols.
- If I didn't need to account for that, I need to simply take the original string, split it into an array, use the reverse and join methods, and check if they're equal to each other.
- I will need to use a.....(loop, sorting algorithm, etc.) to do...... so that .......

</details>

<details style="margin-left: 50px">

  <summary>Brute Force Code</summary>

</details>

<details style="margin-left: 50px">

  <summary>Refactored Code</summary>

  ```js
  const clean = (string) => string.replace(/[\W_]/g, '').toLocaleLowerCase();

  const isPalindrome = (string) => {
    cleanString = clean(string);
    return (
      Array.from(cleanString).toString() ===
      Array.from(cleanString)
        .reverse()
        .toString()
    );
  }
  ```

</details>

<details style="margin-left: 50px">

  <summary>Testing</summary>

```js
  console.log(palindrome("racecar"));
  console.log(palindrome("cicadas"));
```

</details>
</details>

### Date Palindrome

<details><summary>Expand</summary>

> February 2nd, 2020, is a _date_ Palindrome.

<details style="margin-left: 50px">

<summary>Starter Code</summary>

```js
  const isDatePalindrome = (str) => {

  }
```

</details>

<details style="margin-left: 50px">

  <summary>Clarifying Questions</summary>

</details>

<details style="margin-left: 50px">

  <summary>Pseudocode</summary>

</details>

<details style="margin-left: 50px">

  <summary>Brute Force Code</summary>

</details>

<details style="margin-left: 50px">

  <summary>Refactored Code</summary>

</details>

<details style="margin-left: 50px">

  <summary>Testing</summary>

</details>
</details>

***
