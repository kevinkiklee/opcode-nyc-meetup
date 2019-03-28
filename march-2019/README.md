# Operation Code NYC - March 2019 Meetup

## Schedule

* 6:30pm - Socialization and Refreshments
* 6:45pm - Kick-off and Introduction
* 7:00pm - Algorithms!
* 8:15pm - Networking and Closing

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

// For fun
const findMinMax = nums =>
  nums.reduce(([min, max], num) =>
    [Math.min(min, num), Math.max(max, num)],
    [Infinity, -Infinity])
```

### **[Titlecase a Sentence]**

Write a function that returns the provided string with the first letter of each word capitalized.

Return the provided string with the first letter of each word capitalized. Make sure the rest of the word is in lower case.
For the purpose of this exercise, also capitalize connecting words like "the" and "of".

```
titleCase("operation code") should return "Operation Code"
titleCase("fLATiroN HeALTh") should return "Flatiron Health"
```

**Possible Solutions**

```
const titleCase = sentence => {
  let titleCasedSentence = ''

  const words = sentence.split(' ')

  for (let wordIndex = 0; i < words.length; i++) {
    const word = words[wordIndex]
    const chars = word.split('')

    for (let charIndex = 0; j < chars.length; j++) {
      const char = chars[charIndex]

      if (charIndex === 0) {
        titleCasedSentence += char.toUpperCase()
      } else {
        titleCasedSentence += char.toLowerCase()
      }
    }

    titleCaseSentence += ' '
  }

  return titleCasedSentence
}

const titleCase = sentence => {
  let titleCasedSentence = ''
  let shouldUpperCase = true

  for (let i = 0; i < sentence.length; i++) {
    const char = sentence[i]

    if (shouldUpperCase) {
      titleCasedSentence += char.toUpperCase()
    } else {
      titleCasedSentence += char.toLowerCase()
    }

    shouldUpperCase = char === ' '
  }

  return titleCasedSentence
}

const titleCase = sentence =>
  sentence.split(' ').map(word =>
    word.split('').map((char, i) =>
      i === 0 ? char.toUpperCase() : char.toLowerCase()
    ).join('')
  ).join(' ')
```

### **[Factorial]**

Write a function that returns the factorial of a given number `n`.
A factorial is the product of all positive integers from 1 to `n` and is notated with `n!`
Example: `5! = 1 * 2 * 3 * 4 * 5 = 120`

Only integers greater than or equal to zero will be supplied to the function.

```
factorialize(5) should return a number.
factorialize(5) should return 120.
factorialize(10) should return 3628800.
factorialize(20) should return 2432902008176640000.
factorialize(0) should return 1.
```

**Possible Solutions**
```
const findFactorial = n => {
  let product = 1

  for (let num = 2; num <= n; num++) {
    product *= num
  }

  return product
}

const findFactorial = n => {
  if (n === 1) {
    return 1
  }

  return n * findFactorial(n - 1)
}

const findFactorial = n =>
  n === 1 ? 1 : n * findFactorial(n - 1)
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

*[Cellular Automata]*

Eight houses, represented as cells, are arranged in a straight line.
Each day, every cell competes with its adjacent cells (neighbors).
An integer value of 1 represents an active cell and a value of 0 represents an inactive cell.

Rules:
* If the neighbors on both sides of the cell are _same_, the cell becomes _inactive_.
* Otherwise, the cell becomes _active_.

The two cells on each end have a single adjacent cell, so assume that the unoccupied space on the opposite side is an inactive cell.
The state information of all cells should be updated simultaneously.

Write an algorithm to output the state of the cells after the given number of days.

Examples:
```
runCellularAutomata([1, 0, 0, 0, 0, 1, 0, 0], 1) === [0, 1, 0, 0, 1, 0, 1, 0]
runCellularAutomata([1, 1, 1, 0, 1, 1, 1, 1], 2) === [0, 0, 0 ,0, 0, 1, 1, 0]
```

**Possible Solution**

```
const runCellularAutomate = (state, days) => {
  if (days === 0) {
    return state
  }

  const prevState = runCellularAutomate(state, days - 1)

  return prevState.map((cell, i) => {
    const prevCell = i === 0 ? 0 : state[i - 1]
    const nextCell = i === state.length - 1 ? 0 : state[i + 1]

    return prevCell === nextCell ? 0 : 1
  })
}
```

### **[Image Flip]**

Given a binary matrix, we want to flip the image horizontally, then invert it, and return the resulting image.

To flip an image horizontally means that each row of the image is reversed.
For example, flipping `[1, 1, 0]` horizontally results in `[0, 1, 1]`.

To invert an image means that each 0 is replaced by 1, and each 1 is replaced by 0.
For example, inverting `[0, 1, 1]` results in `[1, 0, 0]`.

```
Input: [
  [1,1,0],
  [1,0,1],
  [0,0,0]
]
Output: [
  [1,0,0],
  [0,1,0],
  [1,1,1]
]

Input: [
  [1,1,0,0],
  [1,0,0,1],
  [0,1,1,1],
  [1,0,1,0]
]
Output: [
  [1,1,0,0],
  [0,1,1,0],
  [0,0,0,1],
  [1,0,1,0]
]
```

**Possible Solution**

```
// Time Complexity: O(row*col)
// Space Complexity: O(1)

const flipAndInvertImage = grid => {
  const rowLength = grid.length
  const colLength = grid[0].length

  for (let row = 0; row < rowLength; row += 1) {
    for (let col = 0; col < colLength / 2; col += 1) {
      const oppCol = colLength - 1 - col
      const swap = grid[row][col] ? 0 : 1

      grid[row][col] = grid[row][oppCol] ? 0 : 1
      grid[row][oppCol] = swap
    }
  }

  return grid
};

// Time Complexity: O(row*col)
// Space Complexity: O(row*col)

const flipAndInvertImage = grid =>
  grid.map(row => row.reverse().map(cell => cell ? 0 : 1))
```
