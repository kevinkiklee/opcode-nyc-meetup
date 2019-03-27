# Operation Code NYC - March 2019 Meetup

## No Coding Experience

* Write a function `helloWorld` that prints `Hello, World` to the screen.
* Write a function `greetUser` that takes their name as a parameter and greets them with their name. Example: `Hello, Kevin`
* Modify the previous function such that only the user `OpCode` is greeted.
* Write a function `sumNumbers` that takes a number `N` and prints the sum of the numbers from `1` to `N`

## Beginner
For those who have some experience with loops and branches.

### **[Find the minimum and the maximum]**
Write a function that returns the minimum and the maximum of an unsorted array of integers in the form of `[minimum, maximum]`.
* Do not use the built in `min` or `max` functionality.

Examples:
```
Input: [1, 3, 2, 5, 4]
Output: [1, 5]

Input: [31, 24, 35, 43, 28]
Output: [24, 43]
```

**Possible Solutions**

```
// Time Complexity: O(n) - Linear
// Space Complexity: O(1) - Constant

const findMinMax = inputNumbers => {
  let currentMin = Infinity
  let currentMax = -Infinity

  inputNumbers.forEach(number => {
    if (number < currentMin) {
      currentMin = number
    } else if (number > currentMax) {
      currentMax = number
    }
  })

  return [currentMin, currentMax]
}

// One-liner for fun
const findMinMax = nums => nums.reduce(([min, max], num) => [Math.min(min, num), Math.max(max, num)], [Infinity, -Infinity])
```

## Intermediate

### **[Compare String Sequences]**

Given two strings `S` and `T`, return if they are equal when both are typed into empty text editors. `#` means the backspace character.

```
Input: S = "ab#c", T = "ad#c"
Output: true
* Both S and T become "ac".

Input: S = "ab##", T = "c#d#"
Output: true
* Both S and T become "".

Input: S = "a##c", T = "#a#c"
Output: true
* Both S and T become "c".

Input: S = "a#c", T = "b"
Output: false
* S becomes "c" while T becomes "b".
```

**Possible Solution**

```
const evaluateSequence = sequence => {
  const chars = []

  sequence.split('').forEach(input => {
    if (input === '#') {
      if (chars.length) {
        chars.pop()
      }
    } else {
      chars.push(input)
    }
  })

  return chars.join('')
}

const compareSequences = (S, T) =>
  evaluateSequence(S) === evaluateSequence(T)
```

### **[Count Twos]**

Given an array of integers (both negatives and positives), find the count of each instance of the digit `2` in the array.

```
Input: [-23, -12, 3, 7, 14, 22, 124]
Output: 5
Explanation:  -23, -12, 22 and 124 contain the digit 2
```

**Possible Solution**

```
const countTwos = number => {
  let twoCount = 0

  while (number > 0 || number < 0) {
    const lastDigit = number % 10

    if (lastDigit === 2 || lastDigit === -2) {
      twoCount += 1
    }

    number /= 10
  }

  return twoCount
}
```

## Advanced

### **[Count and Say]**

The count-and-say sequence is the sequence of integers that "counts and says" the previous sequence.

* The sequence starts at `1`
* `1` is read as "one 1" or, literally `11`.
* `11` is read as "two 1s" or `21`.
* `21` is read off as "one 2, then one 1" or `1211`.

```
1. 1
2. 11
3. 21
4. 1211
5. 111221
```

Given an integer `n where `1 ≤ n ≤ 30`, generate the `n`th term of the count-and-say sequence.

```
Input: 1
Output: "1"

Input: 4
Output: "1211"
```

**Possible Solution**
```
const countAndSay = n => {
  if (n === 1) {
    return '1'
  }

  const prevSequence = countAndSay(n - 1)
  const numberChunks = []

  let i = 0

  while (i <= prevSequence.length - 1) {
    let currentMatch = prevSequence[i]
    let j = i + 1

    while (j <= prevSequence.length - 1) {
      if (prevSequence[i] === prevSequence[j]) {
        currentMatch += prevSequence[i]
        j += 1
      } else {
        break
      }
    }

    numberChunks.push(currentMatch)
    currentMatch = ''
    i = j
  }

  return numberChunks.map(chunk => `${chunk.length}${chunk[0]}`).join('')
}
```

