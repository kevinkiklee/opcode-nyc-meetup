# Operation Code NYC - August 2018 Meetup

## Challenges

### No coding

*[Sum of an array]*
Given an array, return the sum of all the elements.

Examples:
```
findArraySum([1]) === 1
findArraySum([1, 2]) === 3
findArraySum([1, 2, 3]) === 6
```

*[Reverse a word]*
Given a word, return the word with the characters reversed.
Examples:
```
findReverse('abc') === 'cba'
findReverse('hello') === 'olleh'
findReverse('world') === 'dlrow'
```

### Easy

*[DNA Compliment]*
In a DNA string, symbols `A` and `T` are complements of each other, as are `C` and `G`.
```
A <-> T
C <-> G
```
Write a function called dnaTransform that takes in a DNA string and returns a string that represents it's compliment.

Examples:
```
findDnaCompliment('AC') === 'TG'
findDnaCompliment('ATCG') === 'TAGC'
findDnaCompliment('GATTACA') === 'CTAATGT'
```

*[Time Convert]*
Given a number of minutes, return the time in `hr:min` format.
* No padding is required.
* The minutes given will range from 0 to 1439

Examples:
```
convertMinutes(0) === '0:0'
convertMinutes(5) === '0:5'
convertMinutes(10) === '0:10'
convertMinutes(60) === '1:0'
convertMinutes(135) === '2:15'
convertMinutes(720) === '12:0'
convertMinutes(800) === '13:20'
convertMinutes(1300) === '21:40'
```

### Easy/Medium

*[Factorial]*
Given a number, return the factorial.
* Solve it both iteratively and recursively.

Examples:
```
findFactorial(0) === 1
findFactorial(1) === 1 === 1
findFactorial(2) === 2 * 1 === 2
findFactorial(3) === 3 * 2 * 1 === 6
findFactorial(4) === 4 * 3 * 2 * 1 === 24
findFactorial(5) === 5 * 4 * 3 * 2 * 1 === 120
```

*[Merge Sorted Arrays]*
Given two sorted arrays, combine both and return a new array that is sorted.

Examples:
```
mergeArrays([1], [2]) === [1, 2]
mergeArrays([1, 2], [3, 4]) === [1, 2, 3, 4]
mergeArrays([1, 3, 5], [2, 4, 6]) === [1, 2, 3, 4, 5, 6]
mergeArrays([1, 1, 2], [2, 3, 3]) === [1, 1, 2, 2, 3, 3]
```

### Medium

*[Digital Root]*
Write a function, `digitalRoot(num)`. It should sum the digits of a positive integer. If it is greater than 10, sum the digits of the resulting number. Keep repeating until there is only one digit in the result, called the `digital root`. _Do not use string conversion within your method._

Examples:
```
digitalRoot(1) # => 1
digitalRoot(22) # => 4
digitalRoot(58) # => 4
```

*[Symmetric Substrings]*
Write a function `findSymmetricSubstrings(string)` that returns an array of substrings that are palindromes. Only include substrings of length > 1.

Examples:
```
findSymmetricSubstrings('hello') === ['ll']
findSymmetricSubstrings('world') === []
findSymmetricSubstrings('aaabbbccc') === ['aaa', 'bbb', 'ccc']
```
