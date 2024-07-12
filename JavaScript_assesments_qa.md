# JavaScript Basis

#### Write a JavaScript program to display the current day and time in the following format.
#### Sample Output : Today is : Friday.
#### Current time is : 4 PM : 50 : 22

```JavaScript
var today = new Date();
var day = today.getDay();

var dayList = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thrusday", "Friday", "Saturday"];

var hour = today.getHours();
var minute = today.getMinutes();
var second = today.getSeconds();

var prepand = (hour >= 12) ? "PM" : "AM";

hour = (hour >= 12) ? hour - 12 : hour;

if(hour === 0 &&  prepand === "PM"){
    if(minute === 0 && second === 0){
        hour = 12;
        prepand = "Noon";
    } else{
        hour = 12;
        prepand = "PM";
    }
}

if(hour === 0 &&  prepand === "AM"){
    if(minute === 0 && second === 0){
        hour = 12;
        prepand = "Midnight";
    } else{
        hour = 12;
        prepand = "AM";
    }
}
document.write("Today is : " + dayList[day] + "<br>");
document.write("Current time is : " + hour + prepand + "&nbsp" + ":" + "&nbsp" + minute + "&nbsp" + ":" + "&nbsp" + second);

```

#### Write a JavaScript program to print the contents of the current window
```JavaScript
// Create a new button element
var button = document.createElement('button');

// Set button text
button.textContent = 'Print Window';

// Set button click event handler
button.addEventListener('click', function() {
    window.print();
});

// Append the button to the document body (or any other element)
document.body.appendChild(button);
```

#### Write a JavaScript program to get the current date.
Expected Output :
mm-dd-yyyy, mm/dd/yyyy or dd-mm-yyyy, dd/mm/yyyy

```JavaScript
const now = new Date();
const day = String(now.getDay()).padStart(2, '0');
const month = String(now.getMonth() + 1).padStart(2, '0');
const year = now.getFullYear();

document.write("mm-dd-yyyy : " + month + '-' + day + '-' + year + '<br>');
document.write("mm/dd/yyyy : " + month + '/' + day + '/' + year + '<br>');
document.write("dd-mm-yyyy : " + day + '-' + month + '-' + year + '<br>');
document.write("dd/mm/yyyy : " + day + '/' + month + '/' + year);
```

#### Write a JavaScript program to find the area of a triangle where lengths of the three of its sides are 5, 6, 7.
```JavaScript
const a = 5;
const b = 6;
const c = 7;

//calculate the semi perimeter
const s = a + b + c / 2;

//calculate the area
const area = Math.sqrt(s * (s - a) * (s - b) * (s - c));

document.write("Area of triangle is : " + area);
```

#### Write a JavaScript program to rotate the string 'w3resource' in right direction by periodically removing one letter from the end of the string and attaching it to the front.
```JavaScript
let str = 'w3resource'; 
function rotateString() { 
str = str[str.length - 1] + str.substring(0, str.length - 1); 
console.log(str); 
} 
// Rotate the string every 500 milliseconds 
setInterval(rotateString, 500);
```

#### Write a JavaScript program to determine whether a given year is a leap year in the Gregorian calendar.
```JavaScript
function isLeapYear(year) {
    if ((year % 4 === 0 && year % 100 !== 0) || (year % 400 === 0)) {
        return true;
    } else {
        return false;
    }
}

// Test the function
const year = 2024;
if (isLeapYear(year)) {
    document.write(year + " is a leap year.");
} else {
    document.write(year + " is not a leap year.");
}
```

#### Write a JavaScript program to find 1st January be a Sunday between 2014 and 2050.
```JavaScript
function firstJanSunday () {
    for(let year = 2014; year <= 2050; year++){
        const date = new Date(year, 0, 1);
        if(date.getDay() === 0){
            document.write("January 1st " + year + "is a Sunday" + "<br>" )
        }
    }
}firstJanSunday();
```

#### Write a JavaScript program where the program takes a random integer between 1 to 10, the user is then prompted to input a guess number. If the user input matches with guess number, the program will display a message "Good Work" otherwise display a message "Not matched".
```JavaScript
// Generate a random number between 1 and 10
const randomNumber = Math.floor(Math.random() * 10) + 1;

// Prompt user to enter a guess number
const userGuess = prompt("Guess a number between 1 and 10:");

// Convert user input from string to integer
const guessNumber = parseInt(userGuess);

// Check if user's guess matches the random number
if (guessNumber === randomNumber) {
    document.write("Good Work!");
} else {
    document.write("Not matched. The correct number was " + randomNumber + ".");
}
```

#### Write a JavaScript program to calculate days left until next Christmas.
```JavaScript
function daysUntilChristmas() {
    // Get today's date
    const today = new Date();

    // Get the current year
    const currentYear = today.getFullYear();

    // Christmas date for this year and next year
    const christmasThisYear = new Date(currentYear, 11, 25); // December is month 11 (0-indexed)
    const christmasNextYear = new Date(currentYear + 1, 11, 25);

    // Calculate time difference in milliseconds
    const diffThisYear = christmasThisYear.getTime() - today.getTime();
    const diffNextYear = christmasNextYear.getTime() - today.getTime();

    // Convert milliseconds to days
    const daysLeftThisYear = Math.ceil(diffThisYear / (1000 * 60 * 60 * 24));
    const daysLeftNextYear = Math.ceil(diffNextYear / (1000 * 60 * 60 * 24));

    // Determine days left until next Christmas
    let daysLeft, nextChristmas;
    if (diffThisYear >= 0) {
        daysLeft = daysLeftThisYear;
        nextChristmas = christmasThisYear;
    } else {
        daysLeft = daysLeftNextYear;
        nextChristmas = christmasNextYear;
    }

    // Output the result
    document.write(`Days left until Christmas (${nextChristmas.toLocaleDateString()}): ${daysLeft}`);
}

// Call the function to calculate and display days until next Christmas
daysUntilChristmas();
```

#### Write a JavaScript program to calculate multiplication and division of two numbers (input from user).
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculate Multiplication and Division</title>
</head>
<body>
    <h5>Calculate Multiplication and Division</h5>
    <form id="calcForm">
        <label for="num1">Enter first number:</label>
        <input type="number" id="num1" name="num1" required><br><br>
        
        <label for="num2">Enter second number:</label>
        <input type="number" id="num2" name="num2" required><br><br>

        <button type="button" onclick="calculate('multiply')">Multiply</button>
        <button type="button" onclick="calculate('divide')">Divide</button>
    </form>

    <div id="result"></div>
</body>
<script src="./srcipt.js"></script>
</html>
```
###### Script.js
```JavaScript
        function calculate(operation) {
            // Get input values
            const num1 = parseInt(document.getElementById('num1').value);
            const num2 = parseInt(document.getElementById('num2').value);

            // Perform calculations based on operation
            let result;
            if (operation === 'multiply') {
                result = num1 * num2;
            } else if (operation === 'divide') {
                result = num1 / num2;
            }

            // Display the result
            document.getElementById('result').innerHTML = `
                <h3>Result:</h3>
                <p>${operation.charAt(0).toUpperCase() + operation.slice(1)}: ${num1} ${operation === 'multiply' ? '*' : '/'} ${num2} = ${result}</p>
            `;
        }
```

#### Write a JavaScript program to convert temperatures to and from celsius, fahrenheit. [ Formula : c/5 = (f-32)/9 [ where c = temperature in celsius and f = temperature in fahrenheit ] 
##### Expected Output : 60°C is 140 °F 45°F is 7.222222222222222°C
```JavaScript
// Function to convert Celsius to Fahrenheit
function celsiusToFahrenheit(celsius) {
    return (celsius * 9 / 5) + 32;
}

// Function to convert Fahrenheit to Celsius
function fahrenheitToCelsius(fahrenheit) {
    return (fahrenheit - 32) * 5 / 9;
}

// Input temperatures
const celsiusInput = 60;
const fahrenheitInput = 45;

// Convert temperatures
const fahrenheitResult = celsiusToFahrenheit(celsiusInput);
const celsiusResult = fahrenheitToCelsius(fahrenheitInput);

// Output the results
document.write(`${celsiusInput}°C is ${fahrenheitResult}°F`);
document.write(`${fahrenheitInput}°F is ${celsiusResult}°C`);
```

#### Write a JavaScript program to get the website URL (loading page).
```JavaScript
// Get the current URL
const currentURL = window.location.href;

// Output the current URL
document.write("The current URL is: " + currentURL);

```

#### Write a JavaScript function that reverse a number. 
Example x = 32243; 
Expected Output : 34223

```JavaScript
function reverseNumber(num) {
    // Convert the number to a string
    const numStr = num.toString();
    
    // Split the string into an array of characters, reverse the array, and join it back into a string
    const reversedStr = numStr.split('').reverse().join('');
    
    // Convert the reversed string back to a number
    const reversedNum = parseInt(reversedStr, 10);
    
    return reversedNum;
}

// Example usage
const x = 32243;
const reversedX = reverseNumber(x);
document.write("Original number:", x);
document.write("Reversed number:", reversedX);
```

#### Write a JavaScript function that checks whether a passed string is palindrome or not? A palindrome is word, phrase, or sequence that reads the same backward as forward, e.g., madam or nurses run.
```JavaScript
function isPalindrome(str) {
    // Remove non-alphanumeric characters and convert to lowercase
    const string = str.replace(/[^a-zA-Z0-9]/g, '').toLowerCase();

    // Reverse the cleaned string
    const reversedStr = string.split('').reverse().join('');

    // Check if the cleaned string is the same as the reversed string
    return string === reversedStr;
}

const testStr = "Racecar";
document.write(`"${testStr}" is a palindrome: ${isPalindrome(testStr)}`);
```

#### Write a JavaScript function that generates all combinations of a string. 
Example string : 'dog'
Expected Output : d,do,dog,o,og,g
```JavaScript
function generateCombinations(str) {
    let combinations = [];

    // Outer loop to pick starting character
    for (let i = 0; i < str.length; i++) {
        // Inner loop to create combinations with the starting character
        for (let j = i + 1; j <= str.length; j++) {
            combinations.push(str.substring(i, j));
        }
    }

    return combinations;
}

const testStr = 'dog';
const result = generateCombinations(testStr);
document.write(result.join(','));
```

#### Write a JavaScript function that returns a passed string with letters in alphabetical order. Example string : 'webmaster' 
Expected Output : 'abeemrstw' 
Assume punctuation and numbers symbols are not included in the passed string.
```JavaScript
function sortStringAlphabetically(str) {
    // Convert the string to an array of characters
    let charArray = str.split('').sort().join('');
    
    return charArray;
}

const exampleStr = 'webmaster';
const charArray = sortStringAlphabetically(exampleStr);
document.write(`Original string: ${exampleStr}`);
document.write(`Sorted string: ${charArray}`);
```

#### Write a JavaScript function that accepts a string as a parameter and converts the first letter of each word of the string in upper case. 
Example string : 'the quick brown fox' 
Expected Output : 'The Quick Brown Fox '
```JavaScript
function capitalizeWords(str) {
    // Split the string into an array of words
    const words = str.split(' ');

    // Capitalize the first letter of each word
    const capitalizedWords = words.map(word => {
        return word.charAt(0).toUpperCase() + word.slice(1);
    });

    // Join the capitalized words back into a single string
    return capitalizedWords.join(' ');
}

const exampleStr = 'the quick brown fox';
const capitalizedStr = capitalizeWords(exampleStr);
console.log(capitalizedStr); // Output: 'The Quick Brown Fox'
```

#### Write a JavaScript function that accepts a string as a parameter and find the longest word within the string. 
Example string : 'Web Development Tutorial' 
Expected Output : 'Development'
```JavaScript
function findLongestWord(str) {
    // Split the string into an array of words
    const words = str.split(' ');

    // Initialize variables
    let longestWord = '';

    // Iterate through each word
    words.forEach(word => {
        // Compare lengths and update longestWord if current word is longer
        if (word.length > longestWord.length) {
            longestWord = word;
        }
    });

    return longestWord;
}

const exampleStr = 'Web Development Tutorial';
const longestWord = findLongestWord(exampleStr);
document.write(`Longest word in "${exampleStr}" is "${longestWord}"`);
```

#### Write a JavaScript function that accepts a string as a parameter and counts the number of vowels within the string. 
Note : As the letter 'y' can be regarded as both a vowel and a consonant, we do not count 'y' as vowel here. 
Example string : 'The quick brown fox' 
Expected Output : 5
```JavaScript
function countVowels(str) {
    // Convert the string to lowercase to handle case insensitivity
    str = str.toLowerCase();
    
    // Define the vowels (excluding 'y')
    const vowels = ['a', 'e', 'i', 'o', 'u'];
    
    // Initialize a counter for vowels
    let count = 0;
    
    // Loop through each character in the string
    for (let i = 0; i < str.length; i++) {
        // Check if the character is a vowel (excluding 'y')
        if (vowels.includes(str[i]) && str[i] !== 'y') {
            count++;
        }
    }
    
    return count;
}
const exampleStr = 'The quick brown fox';
const vowelCount = countVowels(exampleStr);

// Output using document.write
document.write(`Number of vowels in "${exampleStr}": ${vowelCount}`);
```

####  Write a JavaScript function that accepts a number as a parameter and check the number is prime or not.  
```JavaScript
function isPrime(num) {
    if (num <= 1) {
        return false;
    }
    if (num <= 3) {
        return true;
    }
    if (num % 2 === 0 || num % 3 === 0) {
        return false;
    }
    for (let i = 5; i * i <= num; i += 6) {
        if (num % i === 0 || num % (i + 2) === 0) {
            return false;
        }
    }
    return true;
}
const number = 29;
const result = isPrime(number);
console.log(`${number} is ${result ? 'a prime' : 'not a prime'} number.`);
```
####  Write a JavaScript function which accepts an argument and returns the type.
```javascript
function getType(value) {
    return typeof value;
}

// Example usage:
console.log(getType(42));
console.log(getType("hello"));
console.log(getType(true));
console.log(getType(function() {}));
console.log(getType({}));
console.log(getType(undefined));
console.log(getType(null)); 
console.log(getType([])); 
console.log(getType(/regex/));
```
#### Write a JavaScript function which returns the n rows by n columns identity matrix.
```javascript
function createIdentityMatrix(n) {
    const matrix = [];
    for (let i = 0; i < n; i++) {
        const row = [];
        for (let j = 0; j < n; j++) {
            row.push(i === j ? 1 : 0);
        }
        matrix.push(row);
    }
    return matrix;
}

const n = 4;
const identityMatrix = createIdentityMatrix(n);
console.log(identityMatrix);
```
####  Write a JavaScript function which will take an array of numbers stored and find the second lowest and second greatest numbers, respectively.  
```javascript
function findSecondLowestAndGreatest(arr) {
    if (arr.length < 2) {
        return null
    }
    const uniqueArr = [...new Set(arr)];

    uniqueArr.sort((a, b) => a - b);
    const secondLowest = uniqueArr[1];
    const secondGreatest = uniqueArr[uniqueArr.length - 2];
    return {
        secondLowest: secondLowest,
        secondGreatest: secondGreatest
    };
}

const sampleArray = [1, 2, 3, 4, 5];
const result = findSecondLowestAndGreatest(sampleArray);
console.log(`Second Lowest: ${result.secondLowest}, Second Greatest: ${result.secondGreatest}`);
```
#### Write a JavaScript function which says whether a number is perfect. 
```javascript
function isPerfectNumber(num) {
    if (num <= 1) {
        return false;
    }

    let sum = 0;
    for (let i = 1; i < num; i++) {
        if (num % i === 0) {
            sum += i;
        }
    }
    return sum === num;
}

const number = 28;
const result = isPerfectNumber(number);
console.log(`${number} is ${result ? 'a perfect' : 'not a perfect'} number.`); 
```
####  Write a JavaScript function to compute the factors of a positive integer. 
```javascript
function getFactors(num) {
    if (num <= 0) {
        return "Please enter a positive integer.";
    }

    const factors = [];
    for (let i = 1; i <= num; i++) {
        if (num % i === 0) {
            factors.push(i);
        }
    }
    return factors;
}

const number = 28;
const factors = getFactors(number);
console.log(`Factors of ${number}: ${factors.join(', ')}`); 
```
####  Write a JavaScript function to convert an amount to coins. 
```javascript
function amountToCoins(amount, coins) {
    if (amount <= 0) {
        return [];
    }

    const result = [];
    for (let i = 0; i < coins.length; i++) {
        while (amount >= coins[i]) {
            amount -= coins[i];
            result.push(coins[i]);
        }
    }
    return result;
}
const amount = 46;
const coins = [25, 10, 5, 2, 1];
const coinDistribution = amountToCoins(amount, coins);
console.log(`Amount ${amount} can be converted to coins: ${coinDistribution.join(', ')}`); 
```
####  Write a JavaScript function to compute the value of bn where n is the exponent and b is the bases. Accept b and n from the user and display the result.  
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Exponent Calculator</title>
</head>
<body>
    <h1>Exponent Calculator</h1>
    <label for="base">Base (b):</label>
    <input type="number" id="base" name="base"><br><br>
    <label for="exponent">Exponent (n):</label>
    <input type="number" id="exponent" name="exponent"><br><br>
    <button onclick="calculateExponent()">Calculate</button>
    <p id="result"></p>

    <script src="script.js"></script>
</body>
</html>
```
###### script.js
```javascript
function calculateExponent() {
    const base = parseFloat(document.getElementById('base').value);
    const exponent = parseInt(document.getElementById('exponent').value);
    
    if (isNaN(base) || isNaN(exponent)) {
        document.getElementById('result').innerText = 'Please enter valid numbers for base and exponent.';
        return;
    }

    const result = Math.pow(base, exponent);
    document.getElementById('result').innerText = `Result: ${base}^${exponent} = ${result}`;
}
```
#### Write a JavaScript function to extract unique characters from a string. 
```javscript
function extractUniqueCharacters(str) {
    const uniqueChars = new Set();

    for (const char of str) {
        uniqueChars.add(char);
    }

    return [...uniqueChars].join('');
}

const exampleString = "thequickbrownfoxjumpsoverthelazydog";
const uniqueCharacters = extractUniqueCharacters(exampleString);
console.log(`Unique characters: ${uniqueCharacters}`);
```
####  Write a function for searching JavaScript arrays with a binary search.
```javscript
function binarySearch(arr, target) {
    let left = 0;
    let right = arr.length - 1;

    while (left <= right) {
        const mid = Math.floor((left + right) / 2);

        if (arr[mid] === target) {
            return mid;
        } else if (arr[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    return -1; 
}

// Example usage:
const sortedArray = [1, 2, 3, 4, 5, 6, 7, 8, 9];
const target = 5;
const result = binarySearch(sortedArray, target);

if (result !== -1) {
    console.log(`Element found at index ${result}`);
} else {
    console.log('Element not found in the array');
}
```
####  Write a JavaScript function that returns array elements larger than a number. 
```javascript
function filterLargerThan(arr, num) {
    return arr.filter(element => element > num);
}

const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
const threshold = 5;
const result = filterLargerThan(numbers, threshold);
console.log(result);
```
#### Write a JavaScript function that generates a string id (specified length) of random characters. 
```javascript
function generateRandomId(length) {
    const characters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789';
    let result = '';
    const charactersLength = characters.length;
    
    for (let i = 0; i < length; i++) {
        const randomIndex = Math.floor(Math.random() * charactersLength);
        result += characters.charAt(randomIndex);
    }

    return result;
}

const idLength = 10;
const randomId = generateRandomId(idLength);
console.log(randomId); 
```
#### Write a JavaScript function to get all possible subset with a fixed length (for example 2) combinations in an array.  
```javascript
function getSubsets(arr, subsetLength) {
    const result = [];
    function generateSubset(start, subset) {
        if (subset.length === subsetLength) {
            result.push([...subset]);
            return;
        }
        for (let i = start; i < arr.length; i++) {
            subset.push(arr[i]);
            generateSubset(i + 1, subset);
            subset.pop();
        }
    }
    generateSubset(0, []);
    return result;
}

const array = [1, 2, 3, 4];
const length = 2;
const subsets = getSubsets(array, length);
console.log(subsets
```
####  Write a JavaScript function that accepts two arguments, a string and a letter and the function will count the number of occurrences of the specified letter within the string.  
```javascript
function countOccurrences(str, letter) {
    let count = 0;
    for (let i = 0; i < str.length; i++) {
        if (str[i] === letter) {
            count++;
        }
    }
    return count;
}

const text = "the quick brown fox jumps over the lazy dog";
const targetLetter = "o";
const occurrences = countOccurrences(text, targetLetter);
console.log(`The letter '${targetLetter}' occurs ${occurrences} times in the given string.`); 
```
#### Write a JavaScript function to find the first not repeated character. 
```javascript
function firstNonRepeatedCharacter(str) {
    const charCount = {};
    for (let char of str) {
        if (charCount[char]) {
            charCount[char]++;
        } else {
            charCount[char] = 1;
        }
    }
    for (let char of str) {
        if (charCount[char] === 1) {
            return char;
        }
    }

    return null;
}

const exampleString = "the quick brown fox jumps over the lazy dog";
const firstNonRepeated = firstNonRepeatedCharacter(exampleString);
console.log(firstNonRepeated);
```
####  Write a JavaScript function to apply Bubble Sort algorithm.   
```javscript
function bubbleSort(arr) {
    let len = arr.length;
    for (let i = 0; i < len - 1; i++) {
        for (let j = 0; j < len - 1 - i; j++) {
            if (arr[j] > arr[j + 1]) {
                let temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
    return arr;
}
const array = [64, 34, 25, 12, 22, 11, 90];
console.log("Sorted array:", bubbleSort(array));
```
####  Write a JavaScript function that accept a list of country names as input and returns the longest country name as output.
```javscript
function findLongestCountryName(countryNames) {
    let longestName = "";
    for (let country of countryNames) {
        if (country.length > longestName.length) {
            longestName = country;
        }
    }
    return longestName;
}

const countries = ["Australia", "Germany", "United States of America", "India"];
const longestCountry = findLongestCountryName(countries);
console.log("Longest country name:", longestCountry);
```
#### Write a JavaScript function to find longest substring in a given a string without repeating characters.  
```javascript
function longestUniqueSubstring(str) {
    let maxLength = 0;
    let start = 0;
    let maxSubstring = "";
    let charMap = new Map();

    for (let i = 0; i < str.length; i++) {
        let char = str[i];
        if (charMap.has(char) && charMap.get(char) >= start) {
            start = charMap.get(char) + 1;
        }
        charMap.set(char, i);
        let currentLength = i - start + 1;
        if (currentLength > maxLength) {
            maxLength = currentLength;
            maxSubstring = str.slice(start, i + 1);
        }
    }
    return maxSubstring;
}

const inputString = "abcabcbb";
const longestSubstring = longestUniqueSubstring(inputString);
console.log("Longest unique substring:", longestSubstring);
```
#### Write a JavaScript function that returns the longest palindrome in a given string. 
```javascript
function longestPalindrome(s) {
    if (!s || s.length === 0) return "";
    let longest = "";
    for (let i = 0; i < s.length; i++) {
        let oddPalindrome = expandAroundCenter(s, i, i);
        let evenPalindrome = expandAroundCenter(s, i, i + 1);

        if (oddPalindrome.length > longest.length) longest = oddPalindrome;
        if (evenPalindrome.length > longest.length) longest = evenPalindrome;
    }
    return longest;
}

function expandAroundCenter(s, left, right) {
    while (left >= 0 && right < s.length && s[left] === s[right]) {
        left--;
        right++;
    }
    return s.slice(left + 1, right);
}

const inputString = "babad";
const longestPal = longestPalindrome(inputString);
console.log("Longest palindrome:", longestPal);
```
####  Write a JavaScript program to pass a 'JavaScript function' as parameter. 
```javascript

function higherOrderFunction(callback) {
    console.log("Executing higher-order function...");
    callback();
}

function myCallbackFunction() {
    console.log("Callback function executed!");
}

higherOrderFunction(myCallbackFunction);
```
####  Write a JavaScript function to get the function name.
```javascript
function getFunctionName(func) {
    if (typeof func !== 'function') {
        throw new Error('Parameter must be a function');
    }

    if (func.name) {
        return func.name;
    }
    let funcName = func.toString().match(/^function\s*([^\s(]+)/);
    if (funcName && funcName[1]) {
        return funcName[1];
    }

    throw new Error('Unable to determine function name');
}
function namedFunction() {
    console.log("I'm a named function");
}

let anonymousFunction = function() {
    console.log("I'm an anonymous function");
};

let arrowFunction = () => {
    console.log("I'm an arrow function");
};

console.log(getFunctionName(namedFunction));        
console.log(getFunctionName(anonymousFunction));
console.log(getFunctionName(arrowFunction));  
```
# JavaScript Recursion 
#### Write a JavaScript program to calculate the factorial of a number.  
```javascript
function factorial(n) {
    if (n === 0 || n === 1) {
        return 1;
    } else {
        return n * factorial(n - 1);
    }
}

const number = 5;
console.log(`Factorial of ${number} is: ${factorial(number)}`);
```
####  Write a JavaScript program to find the greatest common divisor (gcd) of two positive numbers. 
```javascript
function gcd(a, b) {
    while (b !== 0) {
        let temp = b;
        b = a % b;
        a = temp;
    }
    return a;
}

// Example usage:
const num1 = 56;
const num2 = 98;
console.log(`GCD of ${num1} and ${num2} is: ${gcd(num1, num2)}`);
```
####  Write a JavaScript program to get the integers in range (x, y). 
```javascript
function range(x, y) {
    let result = [];
    for (let i = x + 1; i < y; i++) {
        result.push(i);
    }
    return result;
}

const x = 2;
const y = 9;
console.log(`Integers in range (${x}, ${y}):`, range(x, y));
```
####  Write a JavaScript program to compute the sum of an array of integers.  
```javascript
function sumArray(arr) {
    return arr.reduce((sum, current) => sum + current, 0);
}

const integers = [1, 2, 3, 4, 5, 6];
console.log(`Sum of the array: ${sumArray(integers)}`);
```
#### Write a JavaScript program to compute the exponent of a number. 
```javascript
function computeExponent(base, exponent) {
    let result = 1;
    for (let i = 0; i < exponent; i++) {
        result *= base;
    }
    return result;
}

const base = 8;
const exponent = 2;
console.log(`${base}^${exponent} = ${computeExponent(base, exponent)}`);
```
#### Write a JavaScript program to get the first n Fibonacci numbers.
```javascript
function getFibonacciNumbers(n) {
    if (n <= 0) return [];
    if (n === 1) return [0];
    
    const fibSequence = [0, 1];
    for (let i = 2; i < n; i++) {
        fibSequence.push(fibSequence[i - 1] + fibSequence[i - 2]);
    }
    return fibSequence;
}

const n = 10;
console.log(`The first ${n} Fibonacci numbers:`, getFibonacciNumbers(n));
```
####  Write a JavaScript program to check whether a number is even or not.
```javascript
function isEven(number) {
    return number % 2 === 0;
}

const number = 4;
console.log(`${number} is even: ${isEven(number)}`);
```
####  Write a JavaScript program for binary search.  
```javascript
Array.prototype.br_search = function(target) {
    let left = 0;
    let right = this.length - 1;

    while (left <= right) {
        const mid = Math.floor((left + right) / 2);
        
        if (this[mid] === target) {
            return mid;
        } else if (this[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    return -1;
};
const sampleArray = [0, 1, 2, 3, 4, 5, 6];
console.log(sampleArray.br_search(5));
console.log(sampleArray.br_search(7));
```
####  Write a merge sort program in JavaScript. 
```javascript
function mergeSort(arr) {
    if (arr.length < 2) return arr;
    const mid = Math.floor(arr.length / 2);
    const left = mergeSort(arr.slice(0, mid));
    const right = mergeSort(arr.slice(mid));
    return merge(left, right);
}

function merge(left, right) {
    let result = [];
    while (left.length && right.length) {
        result.push(left[0] < right[0] ? left.shift() : right.shift());
    }
    return result.concat(left, right);
}
const sampleArray = [38, 27, 43, 3, 9, 82, 10];
console.log("Sorted array:", mergeSort(sampleArray));
```
# JavaScript conditional statements and loops
####  Write a JavaScript program that accept two integers and display the larger. 
```javascript
function findLarger(a, b) {
    if (a > b) {
        return a;
    } else {
        return b;
    }
}
const num1 = 3;
const num2 = -7;
const largerNumber = findLarger(num1, num2);
console.log(`The larger number is: ${largerNumber}`);
```
####  Write a JavaScript conditional statement to find the sign of product of three numbers. Display an alert box with the specified sign.   
```javascript
function findProductSign(a, b, c) {
    const product = a * b * c;
    if (product > 0) {
        alert("The sign is +");
    } else if (product < 0) {
        alert("The sign is -");
    } else {
        alert("The product is zero");
    }
}

findProductSign(3, -7, 2);
findProductSign(1, 5, 2); 
findProductSign(0, -5, 3); 
```
####  Write a JavaScript conditional statement to sort three numbers. Display an alert box to show the result.   
```javascript
function sortThreeNumbers(a, b, c) {
    let temp;
    if (a > b) {
        temp = a;
        a = b;
        b = temp;
    }
    if (a > c) {
        temp = a;
        a = c;
        c = temp;
    }
    if (b > c) {
        temp = b;
        b = c;
        c = temp;
    }
    alert(`Sorted numbers: ${a}, ${b}, ${c}`);
}
sortThreeNumbers(3, 1, 2); 
sortThreeNumbers(0, -1, 5);
sortThreeNumbers(7, 7, 7); 
```
#### Write a JavaScript conditional statement to find the largest of five numbers. Display an alert box to show the result.  
```javascript
function findLargestNumber(a, b, c, d, e) {
    const largest = Math.max(a, b, c, d, e);
    alert(`The largest number is ${largest}`);
}
findLargestNumber(3, 7, 2, 9, 5);  
findLargestNumber(0, -1, 5, 3, 4); 
findLargestNumber(7, 7, 7, 7, 7);
```
####  Write a JavaScript for loop that will iterate from 0 to 15. For each iteration, it will check if the current number is odd or even, and display a message to the screen.   
```javascript
for (let i = 0; i <= 15; i++) {
    const type = (i % 2 === 0) ? 'even' : 'odd';
    console.log(`${i} is ${type}`);
}
```
#### Write a JavaScript program which compute, the average marks of the following students Then, this average is used to determine the corresponding grade.  
```javascript
const students = [
    { name: 'David', marks: 80 },
    { name: 'Vinoth', marks: 77 },
    { name: 'Divya', marks: 88 },
    { name: 'Ishitha', marks: 95 },
    { name: 'Thomas', marks: 68 }
];
function AverageAndGrade(students) {
    let totalMarks = 0;

    for (let student of students) {
        totalMarks += student.marks;
    }
    const averageMarks = totalMarks / students.length;
    let grade;
    if (averageMarks < 60) {
        grade = 'F';
    } else if (averageMarks < 70) {
        grade = 'D';
    } else if (averageMarks < 80) {
        grade = 'C';
    } else if (averageMarks < 90) {
        grade = 'B';
    } else {
        grade = 'A';
    }
    console.log(`Average Marks: ${averageMarks.toFixed(2)}`);
    console.log(`Grade: ${grade}`);
}

AverageAndGrade(students);
```
#### Write a JavaScript program which iterates the integers from 1 to 100. But for multiples of three print "Fizz" instead of the number and for the multiples of five print "Buzz". For numbers which are multiples of both three and five print "FizzBuzz".  
```javascript
for (let i = 1; i <= 100; i++) {
    if (i % 3 === 0 && i % 5 === 0) {
        console.log("FizzBuzz");
    } else if (i % 3 === 0) { 
        console.log("Fizz");
    } else if (i % 5 === 0) {
        console.log("Buzz");
    } else {
        console.log(i);
    }
}
```
#### According to Wikipedia a happy number is defined by the following process :  "Starting with any positive integer, replace the number by the sum of the squares of its digits, and repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1. Those numbers for which this process ends in 1 are happy numbers, while those that do not end in 1 are unhappy numbers (or sad numbers)".  Write a JavaScript program to find and print the first 5 happy numbers. 
```javascript
function isHappyNumber(num) {
    let seen = new Set();

    while (num !== 1 && !seen.has(num)) {
        seen.add(num);
        num = sumOfSquaresOfDigits(num);
    }

    return num === 1;
}
function sumOfSquaresOfDigits(num) {
    let sum = 0;
    while (num > 0) {
        let digit = num % 10;
        sum += digit * digit;
        num = Math.floor(num / 10);
    }
    return sum;
}
function findFirstNHappyNumbers(n) {
    const happyNumbers = [];
    let currentNumber = 1;

    while (happyNumbers.length < n) {
        if (isHappyNumber(currentNumber)) {
            happyNumbers.push(currentNumber);
        }
        currentNumber++;
    }

    return happyNumbers;
}

const first5HappyNumbers = findFirstNHappyNumbers(5);
console.log("First 5 Happy Numbers:", first5HappyNumbers);
```
#### Write a JavaScript program to find the armstrong numbers of 3 digits.  
```javascript
function findArmstrongNumbers() {
    const armstrongNumbers = [];
    for (let num = 100; num <= 999; num++) {
        let sum = 0;
        let temp = num;
        while (temp > 0) {
            let digit = temp % 10;
            sum += digit * digit * digit;
            temp = Math.floor(temp / 10);
        }

        if (sum === num) {
            armstrongNumbers.push(num);
        }
    }

    return armstrongNumbers;
}
const armstrongNumbers = findArmstrongNumbers();
console.log("Armstrong Numbers of 3 digits:", armstrongNumbers);
```
####  Write a JavaScript program to construct the following pattern, using a nested 
for loop.  
*   
* *   
* * *   
* * * *   
* * * * * 
```javascript
function printPattern(rows) {
    for (let i = 1; i <= rows; i++) {
        let pattern = '';
        for (let j = 1; j <= i; j++) {
            pattern += '* ';
        }
        console.log(pattern);
    }
}

const rows = 5;
printPattern(rows);
```
#### Write a JavaScript program to compute the greatest common divisor (GCD) of two positive integers.  
```javascript
function gcd(a, b) {
    while (b !== 0) {
        let temp = b;
        b = a % b;
        a = temp;
    }
    return a;
}

const num1 = 24;
const num2 = 36;

const result = gcd(num1, num2);
console.log(`GCD of ${num1} and ${num2} is:`, result);
```
####  Write a JavaScript program to sum the multiples of 3 and 5 under 1000.  
```javascript
function sumMultiplesOf3And5(limit) {
    let sum = 0;
    for (let i = 1; i < limit; i++) {
        if (i % 3 === 0 || i % 5 === 0) {
            sum += i;
        }
    }
    return sum;
}
const limit = 1000;
const result = sumMultiplesOf3And5(limit);
console.log(`Sum of multiples of 3 and 5 below ${limit} is:`, result);
```
# JavaScript array 
#### Write a JavaScript function to check whether an `input` is an array or not.  
Test Data : 
console.log(is_array('w3resource'));  
console.log(is_array([1, 2, 4, 0])); 
false 
true
```javascript
function is_array(input) {
    return Array.isArray(input);
}
console.log(is_array('w3resource')); 
console.log(is_array([1, 2, 4, 0])); 
```
####  Write a JavaScript function to clone an array.  
Test Data : 
console.log(array_Clone([1, 2, 4, 0]));  
console.log(array_Clone([1, 2, [4, 0]])); 
[1, 2, 4, 0]  
[1, 2, [4, 0]] 
```javascript
function array_Clone(arr) {
    if (!Array.isArray(arr)) {
        return null;
    }
    let clonedArray = [];

    for (let i = 0; i < arr.length; i++) {
        if (Array.isArray(arr[i])) {
            clonedArray.push(array_Clone(arr[i]));
        } else {
            clonedArray.push(arr[i]);
        }
    }
    return clonedArray;
}

console.log(array_Clone([1, 2, 4, 0]));       
console.log(array_Clone([1, 2, [4, 0]]));   
```
####  Write a JavaScript function to get the first element of an array. Passing a parameter 'n' will return the first 'n' elements of the array.  
```javascript
function firstElements(arr, n = 1) {
    if (!Array.isArray(arr)) {
        return null;
    }
    if (n > 0) {
        return arr.slice(0, n);
    } else {
        return arr.slice(0, 1);
    }
}

// Test cases
console.log(firstElements([1, 2, 3, 4, 5]));    
console.log(firstElements([1, 2, 3, 4, 5], 3));
console.log(firstElements([1, 2, 3, 4, 5], 0)); 
console.log(firstElements([1, 2, 3, 4, 5], -1)); 
console.log(firstElements([], 2));             
console.log(firstElements(123));    
```
####  Write a JavaScript function to get the last element of an array. Passing a parameter 'n' will return the last 'n' elements of the array. 
```javascript
function lastElements(arr, n = 1) {
    if (!Array.isArray(arr)) {
        return null;
    }

    if (n > 0) {
        return arr.slice(-n);
    } else {
        return arr.slice(-1);
    }
}
console.log(lastElements([7, 9, 0, -2]));      
console.log(lastElements([7, 9, 0, -2],3));   
console.log(lastElements([7, 9, 0, -2],6));                       
```
####  Write a simple JavaScript program to join all elements of the following array into a string. 
```javascript
let myColor = ["Red", "Green", "White", "Black"];

let outputComma = myColor.join(',');
console.log(outputComma);

let outputPlus = myColor.join('+');
console.log(outputPlus);
```
####  Write a JavaScript program which accept a number as input and insert dashes (-) between each two even numbers. For example if you accept 025468 the output should be 0-254-6-8.
```javascript
function insertDashes(input) {
    let output = '';
    
    for (let i = 0; i < input.length; i++) {
        let currentChar = input[i];
        let nextChar = input[i + 1];
        
        if (parseInt(currentChar) % 2 === 0 && parseInt(nextChar) % 2 === 0) {
            output += currentChar + '-';
        } else {
            output += currentChar;
        }
    }
    return output;
}

let input = '025468';
let result = insertDashes(input);
console.log(result);
```
####  Write a JavaScript program to sort the items of an array.  
```javascript
function sortArray(arr) {
    arr.sort(function(a, b) {
        return a - b;
    });

    let sortedString = arr.join(',');

    return sortedString;
}

let arr1 = [3, 8, 7, 6, 5, -4, 3, 2, 1];

let sortedOutput = sortArray(arr1);
console.log(sortedOutput);
```
####  Write a JavaScript program to find the most frequent item of an array.  
```javascript
function findMostFrequent(arr) {
    if (arr.length === 0)
        return null;

    let frequency = {};
    arr.forEach(function(item) {
        if (frequency[item]) {
            frequency[item]++;
        } else {
            frequency[item] = 1;
        }
    });

    let mostFrequent = null;
    let maxCount = 0;
    for (let item in frequency) {
        if (frequency[item] > maxCount) {
            mostFrequent = item;
            maxCount = frequency[item];
        }
    }

    return `${mostFrequent} ( ${maxCount} times )`;
}

let arr1 = [3, 'a', 'a', 'a', 2, 3, 'a', 3, 'a', 2, 4, 9, 3];

let result = findMostFrequent(arr1);
console.log(result);
```
#### Write a JavaScript program which accept a string as input and swap the case of each character. For example if you input 'The Quick Brown Fox' the output should be 'tHE qUICK bROWN fOX'. 
```javascript
function swapCase(str) {
    let swapped = '';
    for (let i = 0; i < str.length; i++) {
        let char = str[i];
        if (char === char.toUpperCase()) {
            swapped += char.toLowerCase();
        } else {
            swapped += char.toUpperCase();
        }
    }
    return swapped;
}

let inputString = 'The Quick Brown Fox';
let swappedString = swapCase(inputString);
console.log(swappedString); 
```
####  Write a JavaScript program which prints the elements of the following array.  
```javascript
var a = [
    [1, 2, 1, 24],
    [8, 11, 9, 4],
    [7, 0, 7, 27],
    [7, 4, 28, 14],
    [3, 10, 26, 7]
];

for (let i = 0; i < a.length; i++) {
    console.log("row " + i);
    for (let j = 0; j < a[i].length; j++) {
        console.log(" " + a[i][j]);
    }
}
```
####  Write a JavaScript program to find the sum of squares of a numeric vector.  
```javascript
function sumOfSquares(vector) {
    let sum = 0;
    for (let i = 0; i < vector.length; i++) {
        sum += vector[i] * vector[i];
    }
    return sum;
}

const numericVector = [3, 4, 5, 2];
const result = sumOfSquares(numericVector);
console.log("Sum of squares:", result);
```
####  Write a JavaScript program to compute the sum and product of an array of integers. 
```javascript
function computeSumAndProduct(array) {
    let sum = 0;
    let product = 1;
    for (let i = 0; i < array.length; i++) {
        sum += array[i];
        product *= array[i];
    }
    return {
        sum: sum,
        product: product
    };
}
const integers = [1, 2, 3, 4, 5];
const result = computeSumAndProduct(integers);

console.log("Sum:", result.sum);
console.log("Product:", result.product);
```
####  Write a JavaScript program to add items in an blank array and display the items.  
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <title>Add Items to Array</title>
    <style>
        body {
            padding-top: 50px;
        }
    </style>
</head>
<body>
    <input type="text" id="text1">
    <input type="button" id="button1" value="Add" onclick="addElementToArray()">
    <input type="button" id="button2" value="Display" onclick="displayArray()">
    <div id="Result"></div>
</body>
<script src="./scrip.js"></script>
</html>
```
###### script.js
```javascript
// Initialize a variable 'x' with 0
let x = 0;
const array = [];

const addElementToArray = () => {
    array[x] = document.getElementById("text1").value;
    alert(`Element: ${array[x]} added at index ${x}`);
    x++;
    document.getElementById("text1").value = "";
};

const displayArray = () => {
    let result = "<hr/>"; // Initialize a string with a horizontal line
    array.forEach((element, y) => {
        result += `Element ${y} = ${element}<br/>`;
    });
    document.getElementById("Result").innerHTML = result;
};
```
#### Write a JavaScript program to remove duplicate items from an array (ignore case sensitivity). 
```javascript
function removeDuplicatesIgnoreCase(arr) {
    let uniqueMap = new Map();
    arr.forEach(item => {
        uniqueMap.set(item.toLowerCase(), item);
    });
    let uniqueArray = Array.from(uniqueMap.values());

    return uniqueArray;
}

let originalArray = ["apple", "Banana", "Orange", "banana", "orange", "grapes", "APPLE"];
let uniqueArray = removeDuplicatesIgnoreCase(originalArray);
console.log("Original Array:", originalArray);
console.log("Array with duplicates removed (ignore case):", uniqueArray);
```
####  We have the following arrays :  
color = ["Blue ", "Green", "Red", "Orange", "Violet", "Indigo", "Yellow "]; 
o = ["th","st","nd","rd"] 
Write a JavaScript program to display the colors in the following way : 
"1st choice is Blue ." 
"2nd choice is Green." 
"3rd choice is Red.
```javascript
let color = ["Blue", "Green", "Red", "Orange", "Violet", "Indigo", "Yellow"];
let o = ["th", "st", "nd", "rd"];

function displayChoices(colors) {
    for (let i = 0; i < colors.length; i++) {
        let suffix;
        if (i + 1 === 1) {
            suffix = o[1]; // 1st
        } else if (i + 1 === 2) {
            suffix = o[2]; // 2nd
        } else if (i + 1 === 3) {
            suffix = o[3]; // 3rd
        } else {
            suffix = o[0];
        }
        console.log(`${i + 1}${suffix} choice is ${colors[i]}.`);
    }
}

displayChoices(color);
```
#### Find the leap years in a given range of years.  
```javascript
function findLeapYears(startYear, endYear) {
    let leapYears = [];
    for (let year = startYear; year <= endYear; year++) {
        if ((year % 4 === 0 && year % 100 !== 0) || year % 400 === 0) {
            leapYears.push(year);
        }
    }
    return leapYears;
}

let startYear = 2000;
let endYear = 2024;
let result = findLeapYears(startYear, endYear);

console.log(`Leap years between ${startYear} and ${endYear}:`);
console.log(result);
```
#### Write a JavaScript program to shuffle an array. 
```javascript
function shuffleArray(array) {
    let shuffledArray = array.slice();

    for (let i = shuffledArray.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [shuffledArray[i], shuffledArray[j]] = [shuffledArray[j], shuffledArray[i]];
    }

    return shuffledArray;
}

const originalArray = [1, 2, 3, 4, 5];
const shuffledResult = shuffleArray(originalArray);

console.log("Original Array:", originalArray);
console.log("Shuffled Array:", shuffledResult);
```
#### Write a JavaScript program to perform a binary search. 
```javascript
function binarySearch(items, value) {
    let startIndex = 0;
    let endIndex = items.length - 1;

    while (startIndex <= endIndex) {
        let middleIndex = Math.floor((startIndex + endIndex) / 2);

        if (items[middleIndex] === value) {
            return middleIndex; 
        } else if (items[middleIndex] < value) {
            startIndex = middleIndex + 1;
        } else {
            endIndex = middleIndex - 1;
        }
    }
    return -1;
}
const items = [1, 2, 3, 4, 5, 7, 8, 9];
console.log(binarySearch(items, 1)); 
console.log(binarySearch(items, 5));
```
#### There are two arrays with individual values, write a JavaScript program to compute the sum of each individual index value from the given arrays.  
```javascript
function computeArraySum(array1, array2) {
    let maxLength = Math.max(array1.length, array2.length);
    let result = [];
    for (let i = 0; i < maxLength; i++) {
        let sum = (array1[i] || 0) + (array2[i] || 0);
        result.push(sum);
    }
    return result;
}

let array1 = [1, 0, 2, 3, 4];
let array2 = [3, 5, 6, 7, 8, 13];

let output = computeArraySum(array1, array2);
console.log(output);
```
####  Write a JavaScript program to find duplicate values in a JavaScript array. 
```javascript
function findDuplicates(array) {
    let duplicates = [];
    let seen = new Set();

    for (let i = 0; i < array.length; i++) {
        let value = array[i];

        if (seen.has(value)) {
            duplicates.push(value);
        } else {
            seen.add(value);
        }
    }
    return duplicates;
}
let array1 = [1, 2, 3, 4, 2, 7, 8, 3, 7];
let array2 = ['a', 'b', 'c', 'b', 'd', 'e', 'a', 'f', 'c'];

let duplicates1 = findDuplicates(array1);
let duplicates2 = findDuplicates(array2);

console.log('Duplicates in array1:', duplicates1); 
console.log('Duplicates in array2:', duplicates2); 
```
#### Write a JavaScript program to flatten a nested (any depth) array. If you pass shallow, the array will only be flattened a single level.  
```javascript
function flatten(array, shallow = false) {
    let result = [];
    array.forEach(item => {
        if (Array.isArray(item) && !shallow) {
            result.push(...flatten(item));
        } else {
            result.push(item);
        }
    });
    return result;
}

console.log(flatten([1, [2], [3, [[4]]], [5, 6]])); 
console.log(flatten([1, [2], [3, [[4]]], [5, 6]], true));
```
####  Write a JavaScript program to compute the union of two arrays.  
```javascript
function union(array1, array2) {
    let unionSet = new Set([...array1, ...array2]);
    return [...unionSet];
}

console.log(union([1, 2, 3], [100, 2, 1, 10])); 
```
#### Write a JavaScript function to find the difference of two arrays.  
```javascript
function difference(array1, array2) {
    let set1 = new Set(array1);
    let set2 = new Set(array2);
    
    let diffArray = [...array1.filter(x => !set2.has(x)), ...array2.filter(x => !set1.has(x))];
    return diffArray;
}

console.log(difference([1, 2, 3], [100, 2, 1, 10]));  
console.log(difference([1, 2, 3, 4, 5], [1, [2], [3, [[4]]],[5,6]])); 
console.log(difference([1, 2, 3], [100, 2, 1, 10]));
```
####  Write a JavaScript function to remove. 'null', '0', '""', 'false', 'undefined' and 'NaN' values from an array.  
```javascript
function cleanArray(arr) {
    return arr.filter(function (value) {
        return value !== null && value !== 0 && value !== "" && value !== false && value !== undefined && !Number.isNaN(value);
    });
}
var array = [NaN, 0, 15, false, -22, '', undefined, 47, null];
var cleanedArray = cleanArray(array);
console.log(cleanedArray); 
```
####  Write a JavaScript function to sort the following array of objects by title value.
```javascript
var library = [
    { author: "Bill Gates", title: "The Road Ahead", libraryId: 1254 },
    { author: "Steves Jobs", title: "Walter Issacson", libraryId: 4264 },
    { author: "Suzanne Collins", title: "Mockingjay: The Final Book of The Hunger Games",  libraryID: 3245 }
];
function sortByTitle(arr) {
    arr.sort(function (a, b) {
        var titleA = a.title.toLowerCase();
        var titleB = b.title.toLowerCase();

        if (titleA < titleB) {
            return -1;
        }
        if (titleA > titleB) {
            return 1;
        }
        return 0;
    });
    return arr; 
}
var sortedBooks = sortByTitle(library);
console.log(sortedBooks);
```
####  Write a JavaScript program to find a pair of elements (indices of the two numbers) from an given array whose sum equals a specific target number.  
```javascript
function findIndices(numbers, target) {
    let map = {};
    for (let i = 0; i < numbers.length; i++) {
        let currentNum = numbers[i];
        let complement = target - currentNum;

        if (map[complement] !== undefined) {
            return [map[complement], i];
        }
        map[currentNum] = i;
    }
    return "No such pair found";
}
let numbers = [10, 20, 10, 40, 50, 60, 70];
let target = 50;

let result = findIndices(numbers, target);
console.log("Output:", result);
```
#### Write a JavaScript function to retrieve the value of a given property from all elements in an array. 
```javascript
let objArray = [NaN, 0, 15, false, -22, '', undefined, 47, null];

// Extract the numeric values (excluding NaN) from the array
let result = objArray.filter(item => typeof item === 'number' && !isNaN(item));

console.log(result); // Output: [15, -22, 47]
```
#### Write a JavaScript function to find the longest common starting substring in a set of strings.  
```javascript
function longest_common_starting_substring(arr) {
    if (arr.length === 0) return '';
    arr.sort();
    
    let first = arr[0];
    let last = arr[arr.length - 1];
    let len = Math.min(first.length, last.length);
    
    let i = 0;
    while (i < len && first.charAt(i) === last.charAt(i)) {
        i++;
    }
    return first.substring(0, i);
}

console.log(longest_common_starting_substring(['go', 'google'])); 
```
#### Write a JavaScript function to fill an array with values (numeric, string with one character) on supplied bounds.  
```javascript
function num_string_range(start, end, step) {
    let result = [];
    
    if (typeof start === 'number' && typeof end === 'number') {
        for (let i = start; i <= end; i += step) {
            result.push(i);
        }
    } else if (typeof start === 'string' && typeof end === 'string') {
        let startCharCode = start.charCodeAt(0);
        let endCharCode = end.charCodeAt(0);
        
        for (let i = startCharCode; i <= endCharCode; i += step) {
            result.push(String.fromCharCode(i));
        }
    }
    return result;
}

console.log(num_string_range('a', 'z', 2)); 
```
####  Write a JavaScript function to merge two arrays and removes all duplicates elements.  
```javascript
function merge_array(array1, array2) {
    let mergedArray = [];
    array1.forEach(item => {
        if (!mergedArray.includes(item)) {
            mergedArray.push(item);
        }
    });

    array2.forEach(item => {
        if (!mergedArray.includes(item)) {
            mergedArray.push(item);
        }
    });

    return mergedArray;
}

var array1 = [1, 2, 3];
var array2 = [2, 30, 1];

console.log(merge_array(array1, array2));
```
#### Write a JavaScript function to remove a specific element from an array.  
```javascript
function remove_array_element(arr, element) {
    return arr.filter(item => item !== element);
}

console.log(remove_array_element([2, 5, 9, 6], 5));
```
####  Write a JavaScript function to find an array contains a specific element.  
```javascript
function array_contains(arr, element) {
    return arr.includes(element);
}
console.log(array_contains([2, 5, 9, 6], 5));
```
####  Write a JavaScript script to empty an array keeping the original. 
```javascript
let originalArray = [1, 2, 3, 4, 5];
originalArray = [];
console.log(originalArray);
console.log(originalArray.length); 
console.log([1, 2, 3, 4, 5]); 
```
#### Write a JavaScript function to get nth largest element from an unsorted array.  
```javascript
function nthLargest(arr, n) {
    arr.sort(function(a, b) {
        return b - a;
    });
    return arr[n - 1];
}
console.log(nthLargest([43, 56, 23, 89, 88, 90, 99, 652], 4)); // Output: 89
```
####  Write a JavaScript function to get a random item from an array.
```javascript
function getRandomItem(arr) {
    const randomIndex = Math.floor(Math.random() * arr.length);

    return arr[randomIndex];
}

const array = [1, 2, 3, 4, 5];
const randomElement = getRandomItem(array);
console.log(randomElement); 
```
#### Write a JavaScript function to create a specified number of elements with pre-filled numeric value array.  
```javascript
function array_filled(length, value) {
    const filledArray = [];
    for (let i = 0; i < length; i++) {
        filledArray.push(value);
    }
    return filledArray;
}

console.log(array_filled(6, 0));  
console.log(array_filled(4, 11));
```
