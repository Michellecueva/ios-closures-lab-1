# Closures Lab

Fork and clone this repo. On your fork, answer and commit the follow questions. When you are finished, submit the link to your repo on Canvas.

## Question 1

Write a function named `applyKTimes` that takes an integer `K` and a closure and calls the closure K times. The closure will not take any parameters and will not have a return value.

Function Definition:
func applyKTimes(_ K: Int, _ closure: () -> ())

Example:
Input:

```swift
applyKTimes(3) {
    print("Hello Closures!")
}
```
Output:

```swift
Hello Closures!
Hello Closures!
Hello Closures!
```
``` swift


func applyKTimes(_ k: Int, _ closure: () -> ()) {
    for _ in 0..<k {
        closure()
    }
}

```

## Question 2

Use `filter` to create an array called `multiples` that contains all the multiples of 3 from `numbers` and then print it.

`let numbers = [1, 2, 3, 4, 6, 8, 9, 3, 12, 11]`

Example:
Input: `let numbers = [1, 2, 3, 4, 6, 8, 9, 3, 12, 11]`

Expected values: `multiples = [3, 6, 9, 3, 12]`
``` swift 

let multiplesOf3 = numbers.filter({a in a % 3 == 0})

```


## Question 3

Find the largest number from `numbers` and then print it. Use `reduce` to solve this exercise.

Example:
Input: `let numbers = [4, 7, 1, 9, 6, 5, 6, 9]`

Output: `9`
``` swift 

let reduceToFindLargestElement = numbers.reduce(0, {x, y in return x > y ? x: y })

```

## Question 4

Join all the strings from `strings` into one using `reduce`. Add spaces in between strings. Print your result.

Example:
Input: `let strings = ["We", "Heart", "Swift"]`

Output: `"We Heart Swift"`
``` swift 

let sent = strings.reduce(""){$0 + $1 + " "}

```

## Question 5

`let cities = ["Shanghai", "Beijing", "Delhi", "Lagos", "Tianjin", "Karachi", "Karachi", "Tokyo", "Guangzhou", "Mumbai", "Moscow", "São Paulo"]`

a. Use `sortedBy` to sort `cities` in alphabetical order.

b. Use `sortedBy` to sort `cities` alphabetical order of the second character of the city name.

c. Use `sortedBy` to sort `cities` in order of the length of the city name.

``` swift

let sortByFirstLetter = cities.sorted{$0 < $1}

let sortBySecondLetter = cities.sorted{$0.dropFirst() < $1.dropFirst()}

let sortByLength = cities.sorted{$0.count  < $1.count}
```


## Question 6

`let citiesWithPopulation: [(String, Int)] = [("Shanghai", 24256800), ("Beijing", 21516000), ("Delhi", 16787941), ("Lagos", 16060303), ("Tianjin", 15200000), ("Karachi", 14910352), ("Karachi", 14160467), ("Tokyo", 13513734), ("Guangzhou", 13080500), ("Mumbai", 12442373), ("Moscow", 12380664), ("São Paulo", 12038175)]`

a. Use `sortedBy` to sort `citiesWithPopulation` in ascending order of population.

b. Use `sortedBy` to sort `citiesWithPopulation` in reverse alphabetical order of the last character in the city name.

``` swift 

let sortedByPopulation = citiesWithPopulation.sorted{$0.1 < $1.1}

let sortedByLastChar = citiesWithPopulation.sorted{$0.0.suffix(1) > $1.0.suffix(1)}

```


## Question 7

Sort `numbers` in ascending order by the number of divisors. If two numbers have the same number of divisors the order in which they appear in the sorted array does not matter.

`var numbers = [1, 2, 3, 4, 5, 6]`

Example:
Input: `var numbers = [1, 2, 3, 4, 5, 6]`

Output:

```swift
numbers = [1, 2, 3, 5, 4, 6]
// 1 has one divisor
// 2, 3 and 5 have 2
// 4 has 3 divisors
// 6 has 4 divisors

// [1, 5, 2, 3, 4, 6] would also have been a valid solution
```
``` swift 

func divisor(x:Int, y:Int) -> Bool {
    var xcount = 0
    var ycount = 0

    for i in 1...x where x % i == 0 {
        xcount += 1
    }

    for i in 1...y where y % i == 0 {
        ycount += 1
    }

    return xcount < ycount

}

let sortedByDivisor = [1,2,3,4,5,6].sorted(by: divisor)

```

## Question 8

Find the sum of the squares of all the odd numbers from `numbers` and then print it.
``` swift 

`var numbers = [1, 2, 3, 4, 5, 6]`

var sumOfSquares = numbers.map{$0 * $0}.reduce(0,{$0 + $1})


a. Write code that removes all the odd numbers from the array.

var oddNumbers = [Int]()

for i in numbers where i % 2 == 0 {
    oddNumbers.append(i)
}


b. Write code that squares all the numbers in the array.


var numbersSquared = [Int]()

for i in numbers {
    numbersSquared.append(i * i)
}


c. Write code that finds the sum of the array.

var sum = 0

for i in numbers {
    sum += i
}


d. Now use `map`, `filter` and `reduce` to solve this problem.


var sumOfNumbers = numbers.filter{$0 % 2 == 0}

var NumbersSquared = numbers.map{$0 * $0}

var sumOfNumbers = numbers.reduce(0, {$0 + $1})


Example:
Input: `var numbers = [1, 2, 3, 4, 5, 6]`

Output: `35 // 1 + 9 + 25 -> 35`

```

## Question 9

Implement a function `forEach(array: [Int], _ closure: Int -> ())` that takes an array of integers and a closure and runs the closure for each element of the array.

Example:
Function with Input:

```swift
forEach([1, 2, 3, 4]) {
    print($0 * $0)
}
```

``` swift 

func forEach(_ array: [Int], _ closure: (Int) -> ()) {
    for i in array {
        closure(i)
    }
}

```

Output:

```swift
1
4
9
16
```

## Question 10

Implement a function `combineArrays` that takes 2 arrays and a closure that combines 2 Ints into a single Int. The function combines the two arrays into a single array using the provided closure. Assume that the 2 arrays have equal length.

Example:
Input:

```swift
var array1 = [1,2,3,4]
var array2 = [5,5,5,3]
combineArrays(array1,array2) {
    $0 * $1
}
```
``` swift

func combineArrays(_ arr1: [Int], _ arr2: [Int], _ closure: (Int, Int) -> Int) {
    var buildArray = [Int]()
    for i in 0..<arr1.count {
        let result = closure(arr1[i], arr2[i])
        buildArray.append(result)
    }
    print(buildArray)
}

```

Output: `[5,10,15,12]`


## Question 11

a) Write a function called `intsToStrings` that takes an array of Ints and a closure as parameters and returns an array of Strings. The closure should take an Int and return a String. The function should apply the closure to the ints in the array.

`let theInts = [1, 2, 3, 44, 555, 6600, 10763]`

b) Define a closure assigned to a constant called `asString` that just turns an Int to a String and pass it to `intsToStrings`.

c) Define a closure assigned to a constant called `evenOdd` that returns "odd" or "even" if the Int is odd or even and pass it to `intsToStrings`.

d) Define a closure assigned to a constant called `englishWords` that returns the written english word of each digit in an Int, 234 -> "two three four", and pass it to `intsToStrings`.

e) Use the built in `map` method on `theInts` to recreate the answers for b, c and d.

Example:
Input:

```swift
let a = intsToStrings(arr: theInts, toString: asString)
let b = intsToStrings(arr: theInts, toString: evenOdd)
let c = intsToStrings(arr: theInts, toString: englishWords)
```

Output:

```swift
a) ["1", "2", "3", "44", "555", "6600", "10763"]
b) ["odd", "even", "odd", "even", "odd", "even", "odd"]
c) ["one ", "two ", "three ", "four four ", "five five five ", "six six zero zero ", "one zero seven six three "]
```


## Question 12

let myArray = [34,42,42,1,3,4,3,2,49]

a) Sort `myArray` in ascending order by defining the constant `ascendingOrder` below.

```swift
let mySortedArray = myArray.sort(ascendingOrder)
let ascendingOrder =
```

b) Sort `myArray` in descending order by defining the constant `descendingOrder` below.

```swift
let mySecondSortedArray = myArray.sort(descendingOrder)
let descendingOrder =
```


## Question 13

`let arrayOfArrays = [[3,65,2,4],[25,3,1,6],[245,2,3,5,74]]`

a) Sort `arrayOfArrays` in ascending order by the **3rd element** in each array. You can assume each array will have at least 3 elements.

b) Sort `arrayOfArrays` in ascending order by the 3rd element in each array. Don't assume each array will have at least 3 elements. Put all arrays that have less than 3 elements at the end in any order.


## Question 14

```swift
let letterValues = [
"a" : 54,
"b" : 24,
"c" : 42,
"d" : 31,
"e" : 35,
"f" : 14,
"g" : 15,
"h" : 311,
"i" : 312,
"j" : 32,
"k" : 93,
"l" : 203,
"m" : 212,
"n" : 41,
"o" : 102,
"p" : 999,
"q" : 1044,
"r" : 404,
"s" : 649,
"t" : 414,
"u" : 121,
"v" : 838,
"w" : 555,
"x" : 1001,
"y" : 123,
"z" : 432
]
```

a) Sort the string below in descending order according the dictionary `letterValues`:

`var codeString = "aldfjaekwjnfaekjnf"`

b) Sort the string below in ascending order according the dictionary `letterValues`

`var codeStringTwo = "znwemnrfewpiqn"`

## Question 15

```swift
let firstAndLastTuples = [("Johann S.", "Bach"),
("Claudio", "Monteverdi"),
("Duke", "Ellington"),
("W. A.", "Mozart"),
("Nicolai","Rimsky-Korsakov"),
("Scott","Joplin"),
("Josquin","Des Prez")]
```

Sort the array of tuples by last name. Print the sorted array using string interpolation so that the output looks like:

```swift
Bach, Johann S.
Des Prez, Josquin
...etc
```

``` swift 

let sortedArr = firstAndLastTuples.sorted{$0.1 < $1.1}

for tuple in sortedArr {
    print("\(tuple.1), \(tuple.0)")
}

```

## Question 16

a) Write a function called `myFilter` that takes an array of Doubles and a closure as parameters and returns an array of Doubles. The closure should take a Double and return a Bool. The function should apply the closure to the doubles in the array.

`let theDoubles = [11.45, 3.2, 4.0, 5.67, 58.65, 66.0, 5.2, 5.0]`
```swift 

func myFilter(arr: [Double], filter closure: (Double) -> Bool) -> [Double] {
    return arr.filter(closure)
}

```

b) Define a closure assigned to a constant called `biggerThanTen` that takes a double and returns true if it is greater or equal to 10.0 and pass it to `myFilter`.
``` swift 
let biggerThanTen: (Double) -> Bool = {x in
    return x >= 10.0    
}

```

c) Define a closure assigned to a constant called `wholeNumber` that takes a double and returns true if it is a whole number and pass it to `myFilter`.
``` swift 
let wholeNumber: (Double) -> Bool = {x in
    return x.truncatingRemainder(dividingBy: 1.0) == 0
}

```
d) Define a closure assigned to a constant called `justEven` that takes a double and returns true if the number to the left of the point is even and pass it to `myFilter`.

``` swift
let justEven: (Double) -> Bool = {x in
    return floor(x).truncatingRemainder(dividingBy: 2.0) == 0
}

```

e. Use the built in filter method on `theDoubles` to recreate the answers for b, c and d.

``` swift 
let a = theDoubles.filter({$0 >= 10})
let b = theDoubles.filter({$0.truncatingRemainder(dividingBy: 1) == 0})
let c = theDoubles.filter({floor($0).truncatingRemainder(dividingBy: 2) == 0})
```

Example
Input:

```swift
let a = myFilter(arr: theDoubles, filter: biggerThanTen)
let b = myFilter(arr: theDoubles, filter: wholeNumber)
let c = myFilter(arr: theDoubles, filter: justEven)
```

output:

```swift
a. [11.45, 58.65, 66]
b. [4, 66, 5]
c. [4, 58.65, 66]
```
