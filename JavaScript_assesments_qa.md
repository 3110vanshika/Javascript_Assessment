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
###### script.js
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
#### Write a JavaScript function to move an array element from one position to another.  
```javascript
function move(arr, oldIndex, newIndex) {
    if (oldIndex < 0) {
        oldIndex = arr.length + oldIndex;
    }
    if (newIndex < 0) {
        newIndex = arr.length + newIndex;
    }

    const element = arr.splice(oldIndex, 1)[0];
    arr.splice(newIndex, 0, element);

    return arr;
}

console.log(move([10, 20, 30, 40, 50], 0, 2));  
console.log(move([10, 20, 30, 40, 50], -1, -2));
```
####  Write a JavaScript function to filter false, null, 0 and blank values from an array.  
```javascript
function filter_array_values(arr) {
    return arr.filter(item => item);
}
console.log(filter_array_values([58, '', 'abcd', true, null, false, 0])); 
```
#### Write a JavaScript function to generate an array of specified length, filled with integer numbers, increase by one from starting position.  
```javascript
function array_range(start, length) {
    return Array.from({length: length}, (_, i) => start + i);
}
console.log(array_range(1, 4));  
console.log(array_range(-6, 4)); 
```
####  Write a JavaScript function to generate an array between two integers of 1 step length. 
```javascript
function rangeBetween(start, end) {
    return Array.from({ length: end - start + 1 }, (_, i) => start + i);
}
console.log(rangeBetween(4, 7));  
console.log(rangeBetween(-4, 7)); 
```
#### Write a JavaScript function to find the unique elements from two arrays.  
```javascript
function uniqueElements(arr1, arr2) {
    let set1 = new Set(arr1);
    let set2 = new Set(arr2);
    let unionSet = new Set([...set1, ...set2]);
    return [...unionSet];
}

console.log(uniqueElements([1, 2, 3], [100, 2, 1, 10])); 
console.log(uniqueElements([1, 2, 3, 4, 5], [1, [2], [3, [[4]]], [5, 6]])); 
console.log(uniqueElements([1, 2, 3], [100, 2, 1, 10])); 
```
# JavaScript Date
#### Write a JavaScript function to check whether an `input` is a date object or not.  
```javascript
function is_date(input) {
    return Object.prototype.toString.call(input) === '[object Date]';
}
console.log(is_date("October 13, 2014 11:13:00"));  
console.log(is_date(new Date(86400000)));  
console.log(is_date(new Date(99,5,24,11,33,30,0)));  
console.log(is_date([1, 2, 4, 0])); 
```
#### Write a JavaScript function to get the current date.  
```javascript
function curday(separator) {
    var today = new Date();
    var dd = String(today.getDate()).padStart(2, '0');
    var mm = String(today.getMonth() + 1).padStart(2, '0');
    var yyyy = today.getFullYear();

    return mm + separator + dd + separator + yyyy;
}
console.log(curday('/'));
console.log(curday('-'));
```
#### Write a JavaScript function to get the number of days in a month.  
```javascript
function getDaysInMonth(month, year) {
    return new Date(year, month, 0).getDate();
}
console.log(getDaysInMonth(1, 2012)); 
console.log(getDaysInMonth(2, 2012));
console.log(getDaysInMonth(9, 2012)); 
console.log(getDaysInMonth(12, 2012));
```
####  Write a JavaScript function to get the month name from a particular date.  
```javascript
function month_name(date) {
    const monthNames = [
        "January", "February", "March", "April", "May", "June",
        "July", "August", "September", "October", "November", "December"
    ];
    return monthNames[date.getMonth()];
}
console.log(month_name(new Date("10/11/2009")));
console.log(month_name(new Date("11/13/2014")));
```
####  Write a JavaScript function to compare dates (i.e. greater than, less than or equal to).  
```javascript
function compare_dates(date1, date2) {
    if (date1.getTime() === date2.getTime()) {
        return "Date1 = Date2";
    } else if (date1.getTime() > date2.getTime()) {
        return "Date1 > Date2";
    } else {
        return "Date2 > Date1";
    }
}
console.log(compare_dates(new Date('11/14/2013 00:00'), new Date('11/14/2013 00:00'))); 
console.log(compare_dates(new Date('11/14/2013 00:01'), new Date('11/14/2013 00:00'))); 
console.log(compare_dates(new Date('11/14/2013 00:00'), new Date('11/14/2013 00:01')));
```
#### Write a JavaScript function to add specified minutes to a Date object.  
```javascript
function add_minutes(date, minutes) {
    return new Date(date.getTime() + minutes * 60000); 
}

console.log(add_minutes(new Date(2014,10,2), 30).toString());
```
#### Write a JavaScript function to test whether a date is a weekend.  
```javascript
function is_weekend(dateString) {
    const date = new Date(dateString);
    const dayOfWeek = date.getDay();

    if (dayOfWeek === 0 || dayOfWeek === 6) {
        return "weekend";
    } else {
        return undefined;
    }
}
console.log(is_weekend('Nov 15, 2014'));  // Saturday
console.log(is_weekend('Nov 16, 2014'));  // Sunday
console.log(is_weekend('Nov 17, 2014'));  // Monday
```
####  Write a JavaScript function to get difference between two dates in days.  
```javascripr
function date_diff_indays(dateString1, dateString2) {
    const date1 = new Date(dateString1);
    const date2 = new Date(dateString2);
    const timeDiff = Math.abs(date2.getTime() - date1.getTime());
    const diffDays = Math.ceil(timeDiff / (1000 * 3600 * 24));

    return diffDays;
}
console.log(date_diff_indays('04/02/2014', '11/04/2014'));  
console.log(date_diff_indays('12/02/2014', '11/04/2014')); 
```
#### Write a JavaScript function to get the last day of a month.  
```javacscript
function lastday(year, month) {
    const lastDay = new Date(year, month + 1, 0).getDate();
    return lastDay;
}
console.log(lastday(2014, 0)); 
console.log(lastday(2014, 1));  
console.log(lastday(2014, 11));
```
#### Write a JavaScript function to calculate 'yesterday day'.  
```javascript
function yesterday(dateString) {
    let date = new Date(dateString);
    
    date.setDate(date.getDate() - 1);
    
    return date.toString();
}
console.log(yesterday('Nov 15, 2014'));  
console.log(yesterday('Nov 16, 2015')); 
console.log(yesterday('Nov 17, 2016'));
```
#### Write a JavaScript function to get the maximum date from an array of dates.  
```javascript
function max_date(dateArray) {
    let dates = dateArray.map(dateStr => new Date(dateStr));
    let maxDate = new Date(Math.max.apply(null, dates));
    return maxDate.toISOString().slice(0,10).replace(/-/g,"/");
}
console.log(max_date(['2015/02/01', '2015/02/02', '2015/01/03'])); 
```
####  Write a JavaScript function to get the minimum date from an array of dates.  
```javascript
function min_date(dateArray) {
    let dates = dateArray.map(dateStr => new Date(dateStr));
    let minDate = new Date(Math.min.apply(null, dates));
    return minDate.toISOString().slice(0,10).replace(/-/g,"/");
}
console.log(min_date(['2015/02/01', '2015/02/02', '2015/01/03'])); 
```
####  Write a JavaScript function that will return the number of minutes in hours and minutes. 
```javascript
function timeConvert(minutes) {
    if (minutes < 0) {
        return "Please enter a positive number of minutes.";
    }
    let hours = Math.floor(minutes / 60);
    let remainingMinutes = minutes % 60;
    
    let hourString = hours === 1 ? "hour" : "hours";
    let minuteString = remainingMinutes === 1 ? "minute" : "minutes";
    
    return `${minutes} minutes = ${hours} ${hourString} and ${remainingMinutes} ${minuteString}.`;
}
console.log(timeConvert(200)); 
```
#### Write a JavaScript function to get the amount of days of a year.  
```javascript
function daysOfYear(year) {
    if ((year % 4 === 0 && year % 100 !== 0) || year % 400 === 0) {
        return 366;
    } else {
        return 365; 
    }
}
console.log(daysOfYear(2023)); 
console.log(daysOfYear(2024)); 
```
#### Write a JavaScript function to get the quarter (1 to 4) of the year.  
```javascript
function quarter_of_the_year(date) {
    let month = date.getMonth();
    if (month >= 0 && month <= 2) {
        return 1; 
    } else if (month >= 3 && month <= 5) {
        return 2;
    } else if (month >= 6 && month <= 8) {
        return 3; 
    } else {
        return 4; 
    }
}
console.log(quarter_of_the_year(new Date(2015, 1, 21)));
console.log(quarter_of_the_year(new Date(2015, 10, 18)));
```
####  Write a JavaScript function to count the number of days passed since beginning of the year.  
```javascript
function days_passed(date) {
    let startOfYear = new Date(date.getFullYear(), 0, 0);
    let diff = date - startOfYear;
    let oneDay = 1000 * 60 * 60 * 24;
    let daysPassed = Math.floor(diff / oneDay);
    return daysPassed;
}
console.log(days_passed(new Date(2015, 0, 15))); 
console.log(days_passed(new Date(2015, 11, 14))); 
```
#### Write a JavaScript function to convert a Unix timestamp to time.  
```javascript
function days_passed(date) {
    let startOfYear = new Date(date.getFullYear(), 0, 0);
    let diff = date - startOfYear;
    let days = Math.floor(diff / (1000 * 60 * 60 * 24));

    return days;
}
console.log(days_passed(new Date(2015, 0, 15)));  
console.log(days_passed(new Date(2015, 11, 14)));
```
####  Write a JavaScript program to calculate age.  
```javascript
function calculate_age(birthDate) {
    let currentDate = new Date();
    let age = currentDate.getFullYear() - birthDate.getFullYear();
    if (currentDate.getMonth() < birthDate.getMonth() || 
        (currentDate.getMonth() === birthDate.getMonth() && currentDate.getDate() < birthDate.getDate())) {
        age--;
    }
    return age;
}
console.log(calculate_age(new Date(1982, 11, 4))); 
console.log(calculate_age(new Date(1962, 1, 1))); 
```
#### Write a JavaScript function to get the day of the month, 2 digits with leading zeros.   
```javascript
function day_of_the_month(date) {
    let day = date.getDate();
    let formattedDay = String(day).padStart(2, '0');
    return formattedDay;
}
let d = new Date(2015, 10, 1); 
console.log(day_of_the_month(d));
```
#### Write a JavaScript function to get a textual representation of a day (three letters, Mon through Sun).   
```javascript
function short_Days(date) {
    const days = ['Sun', 'Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat'];
    let dayIndex = date.getDay();
    return days[dayIndex];
}
let dt = new Date(2015, 10, 1);
console.log(short_Days(dt)); 
```
####  Write a JavaScript function to get a full textual representation of the day of the week (Sunday through Saturday).   
```javascript
function long_Days(date) {
    const days = ['Sunday', 'Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday'];
    let dayIndex = date.getDay();
    return days[dayIndex];
}
let dt = new Date(2015, 10, 1);  
console.log(long_Days(dt));
```
#### Write a JavaScript function to get ISO-8601 numeric representation of the day of the week (1 (for Monday) to 7 (for Sunday)).   
```javascript
function ISO_numeric_date(date) {
    let isoDay = date.getDay();
    if (isoDay === 0) {
        isoDay = 7; 
    }

    return isoDay;
}
let dt = new Date(2015, 10, 1); 
console.log(ISO_numeric_date(dt)); 
```
####  Write a JavaScript function to get English ordinal suffix for the day of the month, 2 characters (st, nd, rd or th.).   
```javascript
function english_ordinal_suffix(date) {
    let day = date.getDate();
    let suffix = "";

    if (day % 10 === 1 && day !== 11) {
        suffix = "st";
    } else if (day % 10 === 2 && day !== 12) {
        suffix = "nd";
    } else if (day % 10 === 3 && day !== 13) {
        suffix = "rd";
    } else {
        suffix = "th";
    }
    return day + suffix;
}

let dt = new Date(2015, 10, 1);
console.log(english_ordinal_suffix(dt));
```
#### Write a JavaScript function to get ISO-8601 week number of year, weeks starting on Monday.   
```javascript
function ISO8601_week_no(dt) {
    let tdt = new Date(dt.valueOf());
    let dayn = (dt.getDay() + 6) % 7;
    tdt.setDate(tdt.getDate() - dayn + 3);
    let firstThursday = tdt.valueOf();
    tdt.setMonth(0, 1);
    if (tdt.getDay() !== 4) {
        tdt.setMonth(0, 1 + ((4 - tdt.getDay()) + 7) % 7);
    }
    return 1 + Math.ceil((firstThursday - tdt) / 604800000);
}
let dt = new Date(2015, 10, 1);  
console.log(ISO8601_week_no(dt)); 
```
####  Write a JavaScript function to get a full textual representation of a month, such as January or June.   
```javascript
function full_month(dt) {
    const monthNames = [
        "January", "February", "March", "April", "May", "June",
        "July", "August", "September", "October", "November", "December"
    ];
    let monthIndex = dt.getMonth();
    return monthNames[monthIndex];
}
let dt = new Date(2015, 10, 1); 
console.log(full_month(dt)); 
```
#### Write a JavaScript function to get a numeric representation of a month, with leading zeros (01 through 12).   
```javascript
function numeric_month(dt) {
    let monthIndex = dt.getMonth() + 1;
    return monthIndex.toString().padStart(2, '0');
}
let dt = new Date(2015, 10, 1);  
console.log(numeric_month(dt));
```
####  Write a JavaScript function to get a short textual representation of a month, three letters (Jan through Dec).   
```javascript
function short_months(dt) {
    const months = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 
                    'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'];
    let monthIndex = dt.getMonth();
    return months[monthIndex];
}

let dt = new Date(2015, 10, 1); 
console.log(short_months(dt)); 
```
#### Write a JavaScript function to get a full numeric representation of a year (4 digits).   
```javascript
function full_year(dt) {
    return dt.getFullYear();
}

let dt = new Date(2015, 10, 1); 
console.log(full_year(dt));
```
#### Write a JavaScript function to get a two digit representation of a year.   
```javascript
function short_year(dt) {
    let fullYear = dt.getFullYear();
    let twoDigitYear = fullYear.toString().slice(-2);
    return twoDigitYear;
}

let dt = new Date(1989, 10, 1);  
console.log(short_year(dt));  
```
#### Write a JavaScript function to get lowercase Ante meridiem and Post meridiem. 
```javascript
function get_am_pm(dt) {
    let hours = dt.getHours();
    let am_pm = hours >= 12 ? 'pm' : 'am';
    return am_pm;
}

let dt1 = new Date(2021, 7, 21, 10, 30);  
let dt2 = new Date(2021, 7, 21, 15, 45);
console.log(get_am_pm(dt1));      
console.log(get_am_pm(dt2));         
```
####  Write a JavaScript function to get uppercase Ante meridiem and Post meridiem. 
```javascript
function get_AM_PM(dt) {
    let hours = dt.getHours();
    let am_pm = hours >= 12 ? 'PM' : 'AM';
    return am_pm;
}

let dt1 = new Date(2021, 7, 21, 10, 30); 
let dt2 = new Date(2021, 7, 21, 15, 45);
console.log(get_AM_PM(dt1));             
console.log(get_AM_PM(dt2));     
```
####  Write a JavaScript function to swatch Internet time (000 through 999).   
```javacsript
function internet_time(dt) {
    let utcHours = dt.getUTCHours();
    let utcMinutes = dt.getUTCMinutes();
    let utcSeconds = dt.getUTCSeconds();
    let totalSecondsUTC = (utcHours * 3600) + (utcMinutes * 60) + utcSeconds;

    let totalSecondsBMT = totalSecondsUTC + 3600;

    let beats = Math.floor(totalSecondsBMT / 86.4);

    if (beats >= 1000) beats -= 1000;

    return ("000" + beats).slice(-3);
}
let dt1 = new Date(Date.UTC(1989, 10, 1)); 
console.log(internet_time(dt1));

let dt2 = new Date(Date.UTC(2021, 7, 21, 15, 45)); 
console.log(internet_time(dt2));
```
####  Write a JavaScript function to get 12-hour format of an hour with leading zeros.   
```javascript
function hours_with_zeroes(dt) {
    let hours = dt.getHours();
    let hours12 = hours % 12 || 12;
    return ("0" + hours12).slice(-2);
}

let dt = new Date(1989, 10, 1);
console.log(hours_with_zeroes(dt));
```
#### Write a JavaScript function to get 24-hour format of an hour without leading zeros.   
```javascript
function hours_without_zeroes(dt) {
    return dt.getHours();
}
let dt = new Date(1989, 10, 1);
console.log(hours_without_zeroes(dt));
```
####  Write a JavaScript function to get minutes with leading zeros (00 to 59).   
```javascript
function minutes_with_leading_zeros(dt) {
    let minutes = dt.getMinutes();
    return minutes < 10 ? '0' + minutes : minutes.toString();
}

let dt = new Date(1989, 10, 1);
console.log(minutes_with_leading_zeros(dt));  
```
####  Write a JavaScript function to get seconds with leading zeros (00 through 59).   
```javascript
function seconds_with_leading_zeros(dt) {
    let seconds = dt.getSeconds();
    return seconds < 10 ? '0' + seconds : seconds.toString();
}

let dt = new Date(1989, 10, 1);
console.log(seconds_with_leading_zeros(dt)); 
```
#### Write a JavaScript function to get Timezone.   
```javascript
function seconds_with_leading_zeros(dt) 
{ 
  return /\((.*)\)/.exec(new Date().toString())[1];
}
dt = new Date(); 
console.log(seconds_with_leading_zeros(dt)); 
dt = new Date(1989, 10, 1); 
console.log(seconds_with_leading_zeros(dt));
```
####  Write a JavaScript function to find whether or not the date is in daylights savings time.   
```javascript

function daylights_savings(dt) 
{ 
  var dst = null;
  for (var i = 0; i < 12; ++i) 
    {
      var d = new Date(dt.getFullYear(), i, 1);
      var offset = dt.getTimezoneOffset();
      if (dst === null) 
        dst = offset;
      else if (offset < dst) 
         {
           dst = offset; 
           break;
         } 
      else if (offset > dst) 
        break;
         }
return (dt.getTimezoneOffset() == dst) | 0;
}

dt = new Date(); 
console.log(daylights_savings(dt)); 
dt = new Date(1989, 10, 1); 
console.log(daylights_savings(dt));
```
####  Write a JavaScript function to get difference to Greenwich time (GMT) in hours.   
```javascript
function diff_to_GMT(dt) 
{ 
   return (-dt.getTimezoneOffset() < 0 ? '-' : '+') + (Math.abs(dt.getTimezoneOffset() / 60) < 10 ? '0' : '') + (Math.abs(dt.getTimezoneOffset() / 60)) + '00';
}
dt = new Date(); 
console.log(diff_to_GMT(dt)); 
```
#### Write a JavaScript function to get timezone offset in seconds.   
```javascript
function timezone_offset_in_seconds(dt) 
{ 
   return -dt.getTimezoneOffset() * 60;
}

dt = new Date(); 
console.log(timezone_offset_in_seconds(dt)); 
```
#### Write a JavaScript function to add specified years to a date.  
```javascript
function add_years(dt,n) 
 {
 return new Date(dt.setFullYear(dt.getFullYear() + n));      
 }
dt = new Date(2014,10,2);
console.log(add_years(dt, 10).toString());
```
####  Write a JavaScript function to add specified weeks to a date.  
```javascript
function add_weeks(dt, n) 
 {
 return new Date(dt.setDate(dt.getDate() + (n * 7)));      
 }
dt = new Date(2014,10,2);
console.log(add_weeks(dt, 10).toString());
```
####  Write a JavaScript function to add specified months to a date.  
```javascript
function add_months(dt, n) 
 {
 return new Date(dt.setMonth(dt.getMonth() + n));      
 }
dt = new Date(2014,10,2);
console.log(add_months(dt, 10).toString());
```
####  Write a JavaScript function to get time differences in minutes between two dates.  
```javascript
function diff_minutes(dt2, dt1) 
 {
  var diff =(dt2.getTime() - dt1.getTime()) / 1000;
  diff /= 60;
  return Math.abs(Math.round(diff));
 }

dt1 = new Date("October 13, 2014 11:11:00");
dt2 = new Date("October 13, 2014 11:13:00");
console.log(diff_minutes(dt1, dt2));
```
####  Write a JavaScript function to get time differences in hours between two dates.  
```javascript
function diff_hours(dt2, dt1) 
 {
  var diff =(dt2.getTime() - dt1.getTime()) / 1000;
  diff /= (60 * 60);
  return Math.abs(Math.round(diff));
 }

dt1 = new Date("October 13, 2014 08:11:00");
dt2 = new Date("October 13, 2014 11:13:00");
console.log(diff_hours(dt1, dt2));
```
####  Write a JavaScript function to get time differences in days between two dates.  
```javascript
function diff_days(dt2, dt1) 
{
  var diff = (dt2.getTime() - dt1.getTime()) / 1000;
  diff /= (60 * 60 * 24);
  return Math.abs(Math.round(diff));
}
dt1 = new Date("October 13, 2014 08:11:00");
dt2 = new Date("October 19, 2014 11:13:00");
console.log(diff_days(dt1, dt2));
```
#### Write a JavaScript function to get time differences in weeks between two dates.  
```javascript
function diff_weeks(dt2, dt1) 
{
  var diff =(dt2.getTime() - dt1.getTime()) / 1000;
  diff /= (60 * 60 * 24 * 7);
  return Math.abs(Math.round(diff));
}
dt1 = new Date("June 13, 2014 08:11:00");
dt2 = new Date("October 19, 2014 11:13:00");
console.log(diff_weeks(dt1, dt2));
```
#### Write a JavaScript function to get time differences in months between two dates.  
```javascript
function diff_months(dt2, dt1) 
 {
  var diff =(dt2.getTime() - dt1.getTime()) / 1000;
  return Math.abs(Math.round(diff));
  
 }
dt1 = new Date("June 13, 2014 08:11:00");
dt2 = new Date("October 19, 2014 11:13:00");
console.log(diff_months(dt1, dt2));
```
#### Write a JavaScript function to get time differences in years between two dates.  
```javascript
function diff_years(dt2, dt1) 
{
  var diff = (dt2.getTime() - dt1.getTime()) / 1000;
  diff /= (60 * 60 * 24);
  return Math.abs(Math.round(diff / 365.25));
}

dt1 = new Date("June 13, 2014 08:11:00");
dt2 = new Date("October 19, 2017 11:13:00");
console.log(diff_years(dt1, dt2));
```
####  Write a JavaScript function to get the week start date.  
```javascript
function startOfWeek(date)
{
  var diff = date.getDate() - date.getDay() + (date.getDay() === 0 ? -6 : 1);
  return new Date(date.setDate(diff));
}
dt = new Date(); 
console.log(startOfWeek(dt).toString());
```
#### Write a JavaScript function to get the week end date. 
```javascript
function endOfWeek(date)
  {
    var lastday = date.getDate() - (date.getDay() - 1) + 6;
    return new Date(date.setDate(lastday));
  }
dt = new Date(); 
console.log(endOfWeek(dt).toString());
```
#### Write a JavaScript function to get the month start date. 
```javascript
function startOfMonth(date)
{
    return new Date(date.getFullYear(), date.getMonth(), 1);
}

dt = new Date(); 
console.log(startOfMonth(dt).toString());
```
#### Write a JavaScript function to get the month end date.
```javascript
function endOfMonth(date)
  {
  return new Date(date.getFullYear(), date.getMonth() + 1, 0);
  }

dt = new Date(); 
console.log(endOfMonth(dt).toString());
```
# JavaScript String 
####  Write a JavaScript function to check whether an `input` is a string or not.  
```javascript
isString = function (input) {
    if (Object.prototype.toString.call(input) === '[object String]')
        return true;
    else
        return false;
};
console.log(isString('w3resource'));
console.log(isString([1, 2, 4, 0]));
```
#### Write a JavaScript function to check whether a string is blank or not.  
```javascript
function isBlank(input) {
    if (input.length === 0)
        return true;
    else
        return false;
}
console.log(isBlank(''));
console.log(isBlank('abc'));
```
#### Write a JavaScript function to split a string and convert it into an array of words.  
```javascript
function stringToArray (str) {
    return str.trim().split(" ");
};
console.log(stringToArray("Robin Singh"));
```
####  Write a JavaScript function to remove specified number of characters from a string.  
```javascript
function truncateString(str1, length) {
    if ((str1.constructor === String) && (length>0)) {
        return str1.slice(0, length);
    }
};
console.log(truncateString("Abhilash Singh",4));
```
####  Write a JavaScript function to hide email addresses to protect from unauthorized user.  
```javascript
function protectEmail (user_email) {
    var avg, splitted, part1, part2;
    splitted = user_email.split("@");
    part1 = splitted[0];
    avg = part1.length / 2;
    part1 = part1.substring(0, (part1.length - avg));
    part2 = splitted[1];
    return part1 + "...@" + part2;
};

console.log(protectEmail("abhilash_singh@example.com"));
```
####  Write a JavaScript function to parameterize a string.  
```javascript
function parameterizeAString (str1) {
    return str1.trim().toLowerCase().replace(/[^a-zA-Z0-9 -]/, "").replace(/\s/g, "-");
};
console.log(parameterizeAString("Abhilash Singh from India."));
```
####  Write a JavaScript function to capitalize the first letter of a string.  
```javascript
function capitalizeString(str1) {
    return str1.charAt(0).toUpperCase() + str1.slice(1);
}
console.log(capitalizeString('javascript string exercises'));
```
####  Write a JavaScript function to capitalize the first letter of each word in a string.  
```javascript
function capitalizeStringWords(str)
{
  return str.replace(/\w\S*/g, function(txt){return txt.charAt(0).toUpperCase() + txt.substr(1).toLowerCase();});
}
console.log(capitalizeStringWords('javascript string exercises'));
```
#### Write a JavaScript function that takes a string which has lower and upper case letters as a parameter and converts upper case letters to lower case, and lower case letters to upper case.  
```javascript
function string(str) {
    return str.replace(/([a-z]+)|([A-Z]+)/g, function(match, chr) {
        return chr ? match.toUpperCase() : match.toLowerCase();
    });
}
console.log(string('AaBbc'));
```
#### Write a JavaScript function to convert a string into camel case. 
```javascript
function camelizeString(str) {
    return str.replace(/\W+(.)/g, function(match, chr) {
        return chr.toUpperCase();
    });
}

console.log(camelizeString("JavaScript Exercises"));
console.log(camelizeString("JavaScript exercises"));
console.log(camelizeString("JavaScriptExercises"));
```
####  Write a JavaScript function to uncamelize a string.  
```javascript
function uncamelizeString(str, separator) {
    if(typeof(separator) == "undefined") {
      separator = " ";
    }
    var str = str.replace(/[A-Z]/g, function (letter) 
    {
      return separator + letter.toLowerCase();
    });
    return str.replace("/^" + separator + "/", '');
  }
  console.log(uncamelizeString('helloWorld'));
  console.log(uncamelizeString('helloWorld','-'));
  console.log(uncamelizeString('helloWorld','_'));
  ```
####  Write a JavaScript function to concatenates a given string n times (default is 1).  
```javascript
function repeatString(str, count) {
    if (typeof (count) == "undefined") {
        count = 1;
    }
    return count < 1 ? '' : new Array(count + 1).join(str);
}
console.log(repeatString('Ha!'));
console.log(repeatString('Ha!', 2));
console.log(repeatString('Ha!', 3));
```
####  Write a JavaScript function to insert a string within a string at a particular position (default is 1). 
```javascript
function insertString(main_string, ins_string, pos) {
    if(typeof(pos) == "undefined") {
     pos = 0;
   }
    if(typeof(ins_string) == "undefined") {
     ins_string = '';
   }
    return main_string.slice(0, pos) + ins_string + main_string.slice(pos);
 }
 console.log(insertString('We are doing some exercises.'));
 console.log(insertString('We are doing some exercises.','JavaScript '));
 console.log(insertString('We are doing some exercises.','JavaScript ',18));
 ```
####  Write a JavaScript function to humanized number (Formats a number to a human-readable string.) with the correct suffix such as 1st, 2nd, 3rd or 4th.  
```javascript
function humanizeReadableString(num) {
    if (typeof (num) == "undefined") return;
    if (num % 100 >= 11 && num % 100 <= 13)
        return num + "th";
    switch (num % 10) {
        case 1: return num + "st";
        case 2: return num + "nd";
        case 3: return num + "rd";
    }
    return num + "th";
}
console.log(humanizeReadableString());
console.log(humanizeReadableString(1));
console.log(humanizeReadableString(8));
console.log(humanizeReadableString(301));
console.log(humanizeReadableString(402));
```
####  Write a JavaScript function to truncates a string if it is longer than the specified number of characters. Truncated strings will end with a translatable ellipsis sequence ("…") (by default) or specified characters.  
```javascript
function truncateString(str, length, ending) {
    if (length == null) {
      length = 100;
    }
    if (ending == null) {
      ending = '...';
    }
    if (str.length > length) {
      return str.substring(0, length - ending.length) + ending;
    } else {
      return str;
    }
  };
console.log(truncateString('We are doing javascript string exercises.'))
console.log(truncateString('We are doing javascript string exercises.',19))
console.log(truncateString('We are doing javascript string exercises.',15,'!!'))
```
####  Write a JavaScript function to chop a string into chunks of a given length.  
```javascript
function stringChop(str, size){
    if (str == null) return [];
    str = String(str);
    size = ~~size;
return size > 0 ? str.match(new RegExp('.{1,' + size + '}', 'g')) : [str];
}
console.log(stringChop('w3resource'));
console.log(stringChop('w3resource',2));
console.log(stringChop('w3resource',3));
```
#### . Write a JavaScript function to count the occurrence of a substring in a string.  
```javascript
function countSubString(main_str, sub_str) 
{
    main_str += '';
    sub_str += '';
    if (sub_str.length <= 0) 
    {
        return main_str.length + 1;
    }
    subStr = sub_str.replace(/[.*+?^${}()|[\]\\]/g, '\\$&');
    return (main_str.match(new RegExp(subStr, 'gi')) || []).length;
}
console.log(countSubString("The quick brown fox jumps over the lazy dog", 'the'));
console.log(countSubString("The quick brown fox jumps over the lazy dog", 'fox',false));
```
####  Write a JavaScript function to escape a HTML string.  
```javacsript
function escape_HTML(str) {
    return str.replace(/&/g, '&amp;')
        .replace(/</g, '&lt;')
        .replace(/>/g, '&gt;')
        .replace(/"/g, '&quot;')
        .replace(/'/g, '&#39;');
}

console.log(escape_HTML('<a href="javascript-string-exercise-17.php" target="_blank">'));
```
#### Write a JavaScript function that can pad (left, right) a string to get to a determined length. 
```javascript
function formattedString(pad, user_str, pad_pos) {
    if (typeof user_str === 'undefined') 
      return pad;
    if (pad_pos == 'l') {
      return (pad + user_str).slice(-pad.length);
    } 
    else {
      return (user_str + pad).substring(0, pad.length);
    }
  }
  console.log(formattedString('0000',123,'l'));
  console.log(formattedString('00000000',123,''));
  ```
#### Write a JavaScript function to repeat a string a specified times.  
```javascript
function repeat_string(string, count) 
  {
    if ((string == null) || (count < 0) || (count === Infinity) || (count == null))
      {
        return('Error in string or count.');
      }
    count = count | 0;
    return new Array(count + 1).join(string);
  }
console.log(repeat_string('a', 4));
```
####  Write a JavaScript function to get a part of a string after a specified character. 
```javascript
function specifiedCharacter(str, char, pos)
{
  if(pos=='b')
    return str.substring(str.indexOf(char) + 1);
  else if(pos=='a') 
    return str.substring(0, str.indexOf(char));
  else
    return str;  
}
console.log(specifiedCharacter('w3resource: JavaScript Exercises', ':','a'));
console.log(specifiedCharacter('w3resource: JavaScript Exercises', 'E','b'));
```
####  Write a JavaScript function to strip leading and trailing spaces from a string.  
```javascript
function strip(str) {
    return str.replace(/^\s+|\s+$/g, '');
}
console.log(strip('w3resource '));    
console.log(strip(' w3resource'));    
console.log(strip(' w3resource  '));
```
####  Write a JavaScript function to truncate a string to a certain number of words.  
```javascript
function truncate(str, no_words) {
    return str.split(" ").splice(0,no_words).join(" ");
}
console.log(truncate('The quick brown fox jumps over the lazy dog', 4));
```
#### Write a JavaScript function to alphabetize a given string.  
```javascript
function alphabetizeString(str) 
{
    return str.split('').sort().join('').trim();
}
console.log(alphabetizeString('United States'));
```
####  Write a JavaScript function to remove the first occurrence of a given 'search string' from a string.  
```javascript
function alphabetizeString(str) 
{
    return str.split('').sort().join('').trim();
}
console.log(alphabetizeString('United States'));
```
#### Write a JavaScript function to convert ASCII to Hexadecimal format.  
```javascript
function asciiToHexa(str)
{
    var arr1 = [];
    for (var n = 0, l = str.length; n < l; n++)
    {
        var hex = Number(str.charCodeAt(n)).toString(16);
        arr1.push(hex);
    }
    return arr1.join('');
}
console.log(asciiToHexa('12'));
console.log(asciiToHexa('100'));
```
####  Write a JavaScript function to convert Hexadecimal to ASCII format.  
```javascript
function hexToAscii(str1) {
    var hex = str1.toString();
    var str = '';
    for (var n = 0; n < hex.length; n += 2) {
        str += String.fromCharCode(parseInt(hex.substr(n, 2), 16));
    }
    return str;
}
console.log(hexToAscii('3132'));  
console.log(hexToAscii('313030')); 
```
####  Write a JavaScript function to find a word within a string.  
```javascript
function searchWord(text, word){
    var x = 0, y=0;
    for (i=0;i< text.length;i++)
        {
        if(text[i] == word[0])
            {
            for(j=i;j< i+word.length;j++)
               {
                if(text[j]==word[j-i])
                  {
                    y++;
                  }
                if (y==word.length){
                    x++;
                }
            }
            y=0;
        }
    }
   return "'"+word+"' was found "+x+" times.";
}

console.log(searchWord('The quick brown fox', 'fox'));
console.log(searchWord('aa, bb, cc, dd, aa', 'aa'));
```
####  Write a JavaScript function check if a string ends with specified suffix.  
```javascript
function stringSuffix(str, suffix) 
{
    if (((str === null) || (str === '')) || ((suffix === null) || (suffix === '')))
    {
        return false;
    }
    else
    {  
        str = str.toString();
        suffix = suffix.toString();
    }
    return str.indexOf(suffix, str.length - suffix.length) !== -1;
}
console.log(stringSuffix('JS PHP PYTHON', 'PYTHON')); 
console.log(stringSuffix('JS PHP PYTHON', ''))
```
####  Write a JavaScript function to escapes special characters (&, <, >, ', ") for use in HTML. 
```javascript
function escape_html(str) {
    if (str === null || str === '') {
        return false;
    } else {
        str = str.toString();
    }
    var map = {
        '&': '&amp;',
        '<': '&lt;',
        '>': '&gt;',
        '"': '&quot;',
        "'": '&#39;'
    };
    return str.replace(/[&<>"']/g, function(m) { return map[m]; });
}
console.log(escape_html('PHP & MySQL'));
console.log(escape_html('3 > 2')); 
```
####  Write a JavaScript function to remove non-printable ASCII chars.  
```javascript
function removeNonAsciiCharacter(str) {
    if ((str === null) || (str === ''))
        return false;
    else
        str = str.toString();
    return str.replace(/[^\x20-\x7E]/g, '');
}
console.log(removeNonAsciiCharacter('äÄçÇéÉêPHP-MySQLöÖÐþúÚ'));
```
#### Write a JavaScript function to remove non-word characters.  
```javascript
function removeNonWordCharacter (str) {
    if ((str===null) || (str===''))
       return false;
    else
       str = str.toString();
    var PATTERN = /[^\x20\x2D0-9A-Z\x5Fa-z\xC0-\xD6\xD8-\xF6\xF8-\xFF]/g;
    return str.replace(PATTERN, '');
}
console.log(removeNonWordCharacter('PHP ~!@#$%^&*()+`-={}[]|\\:";\'/?><., MySQL'));
```
####  Write a JavaScript function to convert a string to title case.  
```javascript
function stringToTitleCase(str) {
    if ((str === null) || (str === ''))
        return false;
    else
        str = str.toString();
    return str.replace(/\w\S*/g, function (txt) { return txt.charAt(0).toUpperCase() + txt.substr(1).toLowerCase(); });
}
console.log(stringToTitleCase('Js exercises'));
```
####  Write a JavaScript function to remove HTML/XML tags from string.  
```javascript
function removeHtmlTag(str) {
    if ((str === null) || (str === '')) {
        return false;
    } else {
        str = str.toString();
    }
    return str.replace(/<[^>]*>/g, '');
}
console.log(removeHtmlTag('PHP Exercises'));
```
####  Write a JavaScript function to create a Zerofilled value with optional +, - sign.  
```javascript
function zeroFill(number, width, osign) {
    var num = '' + Math.abs(number),
        zerosw = width - num.length,
        sign = number >= 0;
    return (sign ? (osign ? '+' : '') : '-') +
        Math.pow(10, Math.max(0, zerosw)).toString().substr(1) + num;
}

console.log(zeroFill(120, 5, '-')); 
console.log(zeroFill(29, 4));
```
####  Write a JavaScript function to test case insensitive (except special Unicode characters) string comparison.  
```javascript
function caseInsensitiveString(str1, str2) {
    var areEqual = str1.toUpperCase() === str2.toUpperCase();
    return areEqual;
}

console.log(caseInsensitiveString('abcd', 'AbcD')); 
console.log(caseInsensitiveString('ABCD', 'Abce')); 
```
#### Write a JavaScript function to create a case-insensitive search.  
```javascript
function caseInsensitiveSearch(str, search_str) {
    var result = str.search(new RegExp(search_str, "i"));
    if (result > 0)
        return 'Matched';
    else
        return 'Not Matched';
}
console.log(caseInsensitiveSearch('JavaScript Exercises', 'exercises'));
console.log(caseInsensitiveSearch('JavaScript Exercises', 'Exercises'));
console.log(caseInsensitiveSearch('JavaScript Exercises', 'Exercisess'));
```
# JavaScript Validation with regular 
####  Write a JavaScript program to test the first character of a string is uppercase or not. 
```javascript
function uppercaseString(str)
{
   regexp = /^[A-Z]/;
   if (regexp.test(str))
    {
      console.log("String's first character is uppercase");
    } 
    else
    {
      console.log("String's first character is not uppercase");
    }
}
uppercaseString('Abcd');
uppercaseString('abcd');
```
####  Write a JavaScript program to check a credit card number. 
```javascript
function isCreditCardNumber(str)
{
 regexp = /^(?:(4[0-9]{12}(?:[0-9]{3})?)|(5[1-5][0-9]{14})|(6(?:011|5[0-9]{2})[0-9]{12})|(3[47][0-9]{13})|(3(?:0[0-5]|[68][0-9])[0-9]{11})|((?:2131|1800|35[0-9]{3})[0-9]{11}))$/;
  
        if (regexp.test(str))
          {
            return true;
          }
        else
          {
            return false;
          }
}
console.log(isCreditCardNumber("378282246310006"));
console.log(isCreditCardNumber("37828224630006"));
```
#### Write a pattern that matches e-mail addresses.  
```javascript
function validateEmail(str) {
    var mailformat = /^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/;
    if (mailformat.test(str)) {
        console.log("Valid email address!");
    }
    else {
        console.log("You have entered an invalid email address!");
    }
}

validateEmail('me-info@example.com');
```
#### Write a JavaScript program to search a date within a string. 
```javscript
function dateWithString (str)
{
 regexp = /^(1[0-2]|0?[1-9])\/(3[01]|[12][0-9]|0?[1-9])\/(?:[0-9]{2})?[0-9]{2}$/;
  
        if (regexp.test(str))
          {
            return true;
          }
        else
          {
            return false;
          }
}
console.log(dateWithString ("01/01/2015"));
console.log(dateWithString ("01/22/2015"));
console.log(dateWithString ("32/01/2015"));
```
#### Write a JavaScript program that work as a trim function (string) using regular expression. 
```javascript
function Trim(str)
{
  var result;
  if (typeof str === 'string') 
  {
    result = str.replace(/^\s+|\s+$/g, '');
    return result;
  }
  else
  {
    return false;
  }
}
console.log(Trim(' w3resource '));
```
#### Write a JavaScript program to count number of words in string.
```javascript
function countWords(str) {
    str = str.trim();
    str = str.replace(/\s+/g, ' ');
    str = str.replace(/\n /g, '\n');
    var words = str.split(' ');
    words = words.filter(function(word) {
        return word.length > 0;
    });
    return words.length;
}
console.log(countWords("   This is   a   test string.  ")); 
console.log(countWords("Hello\n world!  This  is   a\n  test."));
```
####  Write a JavaScript function to check whether a given value is IP value or not. 
```javascript
function isIp(str)
{
 regexp =  /^(([0-9]|[1-9][0-9]|1[0-9]{2}|2[0-4][0-9]|25[0-5])\.){3}([0-9]|[1-9][0-9]|1[0-9]{2}|2[0-4][0-9]|25[0-5])$|^(([a-zA-Z]|[a-zA-Z][a-zA-Z0-9\-]*[a-zA-Z0-9])\.)*([A-Za-z]|[A-Za-z][A-Za-z0-9\-]*[A-Za-z0-9])$|^\s*((([0-9A-Fa-f]{1,4}:){7}([0-9A-Fa-f]{1,4}|:))|(([0-9A-Fa-f]{1,4}:){6}(:[0-9A-Fa-f]{1,4}|((25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)(\.(25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)){3})|:))|(([0-9A-Fa-f]{1,4}:){5}(((:[0-9A-Fa-f]{1,4}){1,2})|:((25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)(\.(25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)){3})|:))|(([0-9A-Fa-f]{1,4}:){4}(((:[0-9A-Fa-f]{1,4}){1,3})|((:[0-9A-Fa-f]{1,4})?:((25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)(\.(25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)){3}))|:))|(([0-9A-Fa-f]{1,4}:){3}(((:[0-9A-Fa-f]{1,4}){1,4})|((:[0-9A-Fa-f]{1,4}){0,2}:((25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)(\.(25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)){3}))|:))|(([0-9A-Fa-f]{1,4}:){2}(((:[0-9A-Fa-f]{1,4}){1,5})|((:[0-9A-Fa-f]{1,4}){0,3}:((25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)(\.(25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)){3}))|:))|(([0-9A-Fa-f]{1,4}:){1}(((:[0-9A-Fa-f]{1,4}){1,6})|((:[0-9A-Fa-f]{1,4}){0,4}:((25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)(\.(25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)){3}))|:))|(:(((:[0-9A-Fa-f]{1,4}){1,7})|((:[0-9A-Fa-f]{1,4}){0,5}:((25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)(\.(25[0-5]|2[0-4]\d|1\d\d|[1-9]?\d)){3}))|:)))(%.+)?\s*$/;
  
        if (regexp.test(str))
          {
            return true;
          }
        else
          {
            return false;
          }
}
console.log(isIp('198.156.23.5'));
console.log(isIp("172.16.0.1"));
```
#### Write a JavaScript function to count the number of vowels in a given string.  
```javascript
function countVowel(str) {

    return str.match(/[aeiou]/gi).length;
}
console.log(countVowel('The quick brown fox jumps over the lazy dog'));
```
#### . Write a JavaScript function to check whether a given value is an valid url or not. 
```javascript
function isValidUrl(str)
{
  regexp =  /^(?:(?:https?|ftp):\/\/)?(?:(?!(?:10|127)(?:\.\d{1,3}){3})(?!(?:169\.254|192\.168)(?:\.\d{1,3}){2})(?!172\.(?:1[6-9]|2\d|3[0-1])(?:\.\d{1,3}){2})(?:[1-9]\d?|1\d\d|2[01]\d|22[0-3])(?:\.(?:1?\d{1,2}|2[0-4]\d|25[0-5])){2}(?:\.(?:[1-9]\d?|1\d\d|2[0-4]\d|25[0-4]))|(?:(?:[a-z\u00a1-\uffff0-9]-*)*[a-z\u00a1-\uffff0-9]+)(?:\.(?:[a-z\u00a1-\uffff0-9]-*)*[a-z\u00a1-\uffff0-9]+)*(?:\.(?:[a-z\u00a1-\uffff]{2,})))(?::\d{2,5})?(?:\/\S*)?$/;
        if (regexp.test(str))
        {
          return true;
        }
        else
        {
          return false;
        }
}
console.log(isValidUrl("http://www.example.com"));
console.log(isValidUrl("https://www.example.com"));
console.log(isValidUrl("www.example.com"));
```
####  Write a JavaScript function to check whether a given value is alpha numeric or not. 
```javascript
function isAlphaNumeric(str)
{
 regexp = /^[A-Za-z0-9]+$/;
  
        if (regexp.test(str))
          {
            return true;
          }
        else
          {
            return false;
          }
}
console.log(isAlphaNumeric("37828sad"));
console.log(isAlphaNumeric("3243#$sew"));
```
####  Write a JavaScript function to check whether a given value is time string or not. 
```javascript
function isTimeString(str)
{
 regexp = /^(2[0-3]|[01]?[0-9]):([0-5]?[0-9]):([0-5]?[0-9])$/;
  
        if (regexp.test(str))
          {
            return true;
          }
        else
          {
            return false;
          }
}
console.log(isTimeString("11:35:30"));
console.log(isTimeString("90:90:90"));
```
####  Write a JavaScript function to check whether a given value is US zip code or not. 
```javascript
function isUsZipCode(str)
{
 regexp = /^[0-9]{5}(?:-[0-9]{4})?$/;
  
        if (regexp.test(str))
          {
            return true;
          }
        else
          {
            return false;
          }
}
console.log(isUsZipCode("03201-2150"));
console.log(isUsZipCode("7892"));
```
#### Write a JavaScript function to check whether a given value is UK Post Code or not.  
```javascript
function isukPostCode(str)
{
 regexp = /^[A-Z]{1,2}[0-9RCHNQ][0-9A-Z]?\s?[0-9][ABD-HJLNP-UW-Z]{2}$|^[A-Z]{2}-?[0-9]{4}$/;
  
        if (regexp.test(str))
          {
            return true;
          }
        else
          {
            return false;
          }
}
console.log(isukPostCode("B294HJ"));
console.log(isukPostCode("7892"));
```
####  Write a JavaScript function to check whether a given value is Canada Post Code or not.
```javascript
function isCanadaPostCode(str)
{
 regexp = /^(?!.*[DFIOQU])[A-VXY][0-9][A-Z]\s?[0-9][A-Z][0-9]$/;
  
        if (regexp.test(str))
          {
            return true;
          }
        else
          {
            return false;
          }
}
console.log(isCanadaPostCode("K8V3Y1"));
console.log(isCanadaPostCode("K8V 3Y1"));
console.log(isCanadaPostCode("Z4V4X1"));
```
#### Write a JavaScript function to check whether a given value is a social security number or not.  
```javascript
function isSocialSecurityNumber(str)
{
 regexp = /^(?!000|666)[0-8][0-9]{2}-(?!00)[0-9]{2}-(?!0000)[0-9]{4}$/;
        if (regexp.test(str))
          {
            return true;
          }
        else
          {
            return false;
          }
}
console.log(isSocialSecurityNumber("019-90-5680"));
console.log(isSocialSecurityNumber("K8V-3Y1"));
```
####  Write a JavaScript function to check whether a given value is hexadecimal value or not.
```javascript
function isHexadecimal(str)
{
 regexp = /^[0-9a-fA-F]+$/;
  
        if (regexp.test(str))
          {
            return true;
          }
        else
          {
            return false;
          }
}
console.log(isHexadecimal("ffffff"));
console.log(isHexadecimal("fz5500"));
```
####  Write a JavaScript function to check whether a given value is hexcolor value or not.  
```javascript
function isHexcolor(str)
{
 regexp = /^#?([0-9a-fA-F]{3}|[0-9a-fA-F]{6})$/;
  
        if (regexp.test(str))
          {
            return true;
          }
        else
          {
            return false;
          }
}
console.log(isHexcolor("#444"));
console.log(isHexcolor("#3333"));
```
#### Write a JavaScript function to check whether a given value represents a domain or not.
```javascript
function isDomain(str)
{
 regexp = /^[a-z0-9]+([\-\.]{1}[a-z0-9]+)*\.[a-z]{2,6}$/i;
  
        if (regexp.test(str))
          {
            return true;
          }
        else
          {
            return false;
          }
}
console.log(isDomain('www.example.com'));
console.log(isDomain('www.npm.co.uk'));
console.log(isDomain('http://www.example.com'));
console.log(isDomain('https://www.example.com'));
console.log(isDomain('www.example.com'));
```
#### Write a JavaScript function to check whether a given value is html or not.
```javascript
function isHtml(str)
{
 regexp = /<([a-z]+) *[^/]*?>/;
  
        if (regexp.test(str))
          {
            return true;
          }
        else
          {
            return false;
          }
}
console.log(isHtml('<div></div>'));
console.log(isHtml(''));
console.log(isHtml('.selector'));
```
####  Write a JavaScript function to check a given value contains alpha, dash and underscore.
```javascript
function isAlphaDash(str)
{
 regexp = /^[a-z0-9_\-]+$/i;
  
        if (regexp.test(str))
          {
            return true;
          }
        else
          {
            return false;
          }
}
console.log(isAlphaDash('12-133'));
console.log(isAlphaDash('100_23'));
```
####  Write a JavaScript function to print an integer with commas as thousands separators.  
```javascript
function thousandsSeparators(num)
  {
    var num_parts = num.toString().split(".");
    num_parts[0] = num_parts[0].replace(/\B(?=(\d{3})+(?!\d))/g, ",");
    return num_parts.join(".");
  }

console.log(thousandsSeparators(1000));
console.log(thousandsSeparators(10000.23));
console.log(thousandsSeparators(100000));
```
# JavaScript DOM 
#### Here is a sample html file with a submit button. Now modify the style of the paragraph text through javascript code.  
Sample HTML file : 
```html
<!DOCTYPE html>   
<html><br><head>   
<meta charset=utf-8 />   
<title>JS DOM paragraph style</title>   
</head>    
<body>   
<p id ='text'>JavaScript Exercises - w3resource</p>    
<div>   
<button id="jsstyle" onclick="js_style()">Style</button>   
</div>   
</body>   
</html>
``` 
#### Clicking on the button the font, font size, and color of the paragraph text will be changed.
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset=utf-8 />
    <title>JS DOM paragraph style</title>
</head>
<body>
    <p id='text'>JavaScript Exercises - w3resource</p>
    <div>
        <button id="jsstyle" onclick="js_style()">Style</button>
    </div>
</body>
<script src="./script.js"></script>
</html>
```
###### script.js
```javascript
function js_style() 
{
    text.style.fontSize = "14pt";
    text.style.fontFamily = "Comic Sans MS";
    text.style.color = "green";
}
```
#### Write a JavaScript function to get the values of First and Last name of the following form. 
Sample HTML file : 
```html
<!DOCTYPE html>   
<html><head>   
<meta charset=utf-8 />   
<title>Return first and last name from a form - w3resource</title>   
</head><body>   
<form id="form1" onsubmit="getFormvalue()">   
First name: <input type="text" name="fname" value="David"><br>   
Last name: <input type="text" name="lname" value="Beckham"><br>   
<input type="submit" value="Submit">   
</form>   
</body>   
</html>
```
###### html
```html
<!DOCTYPE html>
<html>

<head>
    <meta charset=utf-8 />
    <title>Return first and last name from a form - w3resource</title>
    <style type="text/css">
        body {
            margin: 30px;
        }
    </style>
</head>
<body>
    <form id="form1" onsubmit="getFormvalue()">
        First name: <input type="text" name="fname" value="David"><br>
        Last name: <input type="text" name="lname" value="Beckham"><br>
        <input type="submit" value="Submit">
    </form>
</body>
</html>
```
###### script.js
```javascript
function getFormvalue()
{
  var x=document.getElementById("form1");
  for (var i=0;i<x.length;i++)
  {
    if (x.elements[i].value!='Submit')
    {  
      console.log(x.elements[i].value);
    }  
  }
}
```
####  Write a JavaScript program to set the background color of a paragraph.  
###### html
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset=utf-8 />
    <title>Set the background color of a paragraph</title>
</head>
<body>
    <input type="button" value="Click to set paragraph background color" onclick="set_background()">
    <p>w3resource JavaScript Exercises</p>
    <p>w3resource PHP Exercises</p>
</body>
<script src="./script.js"></script>
</html>
```
###### script.js
```javascript
function set_background() {
  docBody = document.getElementsByTagName("body")[0];
  myBodyElements = docBody.getElementsByTagName("p");
  myp1 = myBodyElements[0];
  myp1.style.background = "rgb(255,0,0)";
  myp2 = myBodyElements[1];
  myp2.style.background = "rgb(255,255,0)";
}
```
####  Here is a sample html file with a submit button. Write a JavaScript function to get the value of the href, hreflang, rel, target, and type attributes of the specified link. 
```html
<!DOCTYPE html>   
<html><head>   
<meta charset=utf-8 />   
</head>   
<body>   
<p><a id="w3r" type="text/html" hreflang="enus" rel="nofollow" target="_self" href="http://www.w3resource.com/">w3reso urce</a></p>   
<button onclick="getAttributes()">Click here to get  attributes value</button>   
</body></html>
```
###### HTML
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset=utf-8 />
    <title>Collect the value of href, hreflang, rel, target, and type attributes of a link</title> 
</head>
<body>
    <p><a id="w3r" type="text/html" hreflang="en-us" rel="nofollow" target="_self" href="https://www.w3resource.com/">w3resource</a></p>
    <button onclick="getAttributes()">Click here to get the attribute's value</button> 
</body>
<script src="./script.js"></script>
</html>
```
###### javascript
```javascript
function getAttributes()
{
    var u = document.getElementById("w3r").href;
    alert('The value of the href attribute of the link is : '+u);
    var v = document.getElementById("w3r").hreflang; 
    alert('The value of the hreflang attribute of the link is : '+v);
    var w = document.getElementById("w3r").rel; 
    alert('The value of the rel attribute of the link is : '+w);
    var x = document.getElementById("w3r").target; 
    alert('The value of the target attribute of the link is : '+x);
    var y = document.getElementById("w3r").type; 
    alert('The value of the type attribute of the link is : '+y);  
}
```
#### Write a JavaScript function to add rows to a table.  
```html
<!DOCTYPE html>   
<html><head><br><meta charset=utf-8 />   
<title>Insert row in a table - w3resource</title>   
</head><body>   
<table id="sampleTable" border="1">   
<tr><td>Row1 cell1</td>   
<td>Row1 cell2</td></tr>   
<tr><td>Row2 cell1</td>   
<td>Row2 cell2</td></tr>   
</table><br>   
<input type="button" onclick="insert_Row()" value="Insert row">    
</body></html>
```
###### html
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset=utf-8 />
    <title>Insert row in a table - w3resource</title>
</head>
<body>
    <table id="sampleTable" border="1">
        <tr>
            <td>Row1 cell1</td>
            <td>Row1 cell2</td>
        </tr>
        <tr>
            <td>Row2 cell1</td>
            <td>Row2 cell2</td>
        </tr>
    </table><br>
    <input type="button" onclick="insert_Row()" value="Insert row">
</body>
<script src="./script.js"></script>
</html>
```
###### javascript
```javascript
function insert_Row()
{
    var x=document.getElementById('sampleTable').insertRow(0);
    var y = x.insertCell(0);
    var z = x.insertCell(1);
    y.innerHTML="New Cell1";
    z.innerHTML="New Cell2";
}
```
#### Write a JavaScript function that accept row, column, (to identify a particular cell) and a string to update the content of that cell.  
```html
<!DOCTYPE html>   
<html><head><br><meta charset=utf-8 />   
<title>Change the content of a cell</title>   
</head><body>   
<table id="myTable" border="1">   
<tr><td>Row1 cell1</td>   
<td>Row1 cell2</td></tr>   
<tr><td>Row2 cell1</td>   
<td>Row2 cell2</td></tr>   
<tr><td>Row3 cell1</td>   
<td>Row3 cell2</td></tr>   
</table><form>   
<input type="button" onclick="changeContent()" value="Change content">   
</form></body></html>
```
###### javascript
```javascript
function changeContent()
{
    rn = window.prompt("Input the Row number(0,1,2)", "0");
    cn = window.prompt("Input the Column number(0,1)","0");
    content = window.prompt("Input the Cell content");  
    var x=document.getElementById('myTable').rows[parseInt(rn,10)].cells;
    x[parseInt(cn,10)].innerHTML=content;
}
```
####  Write a JavaScript function that creates a table, accept row, column numbers from the user, and input row-column number as content (e.g. Row-0 Column-0) of a cell.  
```html
<!DOCTYPE html>   
<html>   
<head>   
<meta charset=utf-8 />   
<title>Change the content of a cell</title>   
<style type="text/css">   
   body {margin: 30px;}   
</style>     
</head><body>   
<table id="myTable" border="1">   
</table><form>   
<input type="button" onclick="createTable()" value="Create the table">   
</form></body></html>
```
###### javascript
```javascript
function createTable()
{
    rn = window.prompt("Input number of rows", 1);
    cn = window.prompt("Input number of columns",1);
    for(var r=0;r<parseInt(rn,10);r++)
    {
        var x=document.getElementById('myTable').insertRow(r);
        for(var c=0;c<parseInt(cn,10);c++)  
        {
            var y=  x.insertCell(c);
            y.innerHTML="Row-"+r+" Column-"+c; 
        }
    }
}
```
####  Write a JavaScript program to remove items from a dropdown list.  
Sample HTML file : 
```html
<!DOCTYPE html>   
<html><head>   
<meta charset=utf-8 />   
<title>Remove items from a dropdown list</title>   
</head><body><form>   
<select id="colorSelect">   
<option>Red</option>   
<option>Green</option>   
<option>White</option>   
<option>Black</option>   
</select>   
<input type="button" onclick="removecolor()" value="Select and Remove"><br
 ></form></body></html>
```
###### javascript
```javascript
function removecolor() {
  var x = document.getElementById("colorSelect");
  x.remove(x.selectedIndex);
}
```
####  Write a JavaScript program to count and display the items of a dropdown list, in an alert window.  
Sample HTML file : 
```html
<!DOCTYPE html>   
<html><head>   
<meta charset=utf-8 />   
<style type="text/css">   
 body {margin: 30px;}   
</style>      
<title>Count and display items of a dropdown list - w3resource</title>   
</head><body><form>   
Select your favorite Color :   
<select id="mySelect">   
<option>Red</option>   
<option>Green</option>   
<option>Blue</option>   
<option>White</option>   
</select>   
<input type="button" onclick="getOptions()" value="Count and Output all items">   
</form></body></html>
```
###### javascript
```javascript
function calculateVolume() {
  var radius = document.getElementById("radius").value;
  if (radius > 0) {
      var volume = (4/3) * Math.PI * Math.pow(radius, 3);
      document.getElementById("volume").value = volume.toFixed(2);
  } else {
      alert("Please enter a positive number for the radius.");
  }
}
```
####  Write a JavaScript program to display a random image (clicking on a button) from the following list.  
###### html
```html
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<title>Display random image</title>
<style>  
    body { padding-top: 30px; }
</style>
</head>
<body>
    <div>
        <button id="jsstyle" onclick="display_random_image();">Show Image</button> 
    </div>
<script src="./script.js"></script>
</body>
</html>
```
###### javascript
```javascript
function display_random_image() 
{
    var theImages = [{
        src: "https://images.pexels.com/photos/1285625/pexels-photo-1285625.jpeg?auto=compress&cs=tinysrgb&w=600",
        width: "240",
        height: "160"
    }, {
        src: "https://images.pexels.com/photos/164336/pexels-photo-164336.jpeg?auto=compress&cs=tinysrgb&w=600",
        width: "320",
        height: "195"
    }, {
        src: "https://images.pexels.com/photos/772689/pexels-photo-772689.jpeg?auto=compress&cs=tinysrgb&w=600",
        width: "500",
        height: "343"
    }];
    var preBuffer = [];
    for (var i = 0, j = theImages.length; i < j; i++) {
        preBuffer[i] = new Image();
        preBuffer[i].src = theImages[i].src;
        preBuffer[i].width = theImages[i].width;
        preBuffer[i].height = theImages[i].height;
    }
    function getRandomInt(min,max) 
    {
        imn = Math.floor(Math.random() * (max - min + 1)) + min;
        return preBuffer[imn];
    }  
    var newImage = getRandomInt(0, preBuffer.length - 1);
    var images = document.getElementsByTagName('img');
    var l = images.length;
    for (var p = 0; p < l; p++) {
        images[0].parentNode.removeChild(images[0]);
    }
    document.body.appendChild(newImage);
}
```
####  Write a JavaScript program to highlight the bold words of the following paragraph, on mouse over a certain link.  
###### html
```html
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Get And Style All Tags</title>
</head>

<body>
    <p>[<a href="#" onMouseOver="highlight()" onMouseOut="return_normal()">On mouse over here bold words of the
            following paragraph will be highlighted</a>]</p>
    <p><strong>We</strong> have just started <strong>this</strong> section for the users (<strong>beginner</strong> to
        intermediate) who <strong>want</strong> to work with <strong>various</strong> JavaScript
        <strong>problems</strong> and write scripts online to <strong>test</strong> their JavaScript
        <strong>skill</strong>.
    </p>
<script src="./script.js"></script>
</body>
</html>
```
###### javascript
```javascript
var bold_Items;
window.onload = getBold_items();
function getBold_items() {
  bold_Items = document.getElementsByTagName('strong');
}
function highlight() {
  for (var i = 0; i < bold_Items.length; i++) {
    bold_Items[i].style.color = "green";
  }
}
function return_normal() {
  for (var i = 0; i < bold_Items.length; i++) {
    bold_Items[i].style.color = "black";
  }
}
```
####  Write a JavaScript program to get the width and height of the window (any time the window is resized). 
###### html
```html
<!doctype html>
<html lang="en">
<head>
    <meta charset=utf-8 />
    <title>Window Size : height and width</title>
</head>
<body onload="getSize()" onresize="getSize()">
    <div id="wh">
    </div>
    <script src="./script.js"></script>
</body>
</html>
```
###### javascript
```javascript
function getSize() {
  var w = document.documentElement.clientWidth;
  var h = document.documentElement.clientHeight;
  document.getElementById('wh').innerHTML = "<h1>Width: " + w + " â€¢ Height: " + h + "</h1>";
}
```
# JavaScript drawing  
#### Write a JavaScript program to draw the following rectangular shape. 
###### html
```html
<!doctype html>
<html>
<head>
    <meta charset=utf-8 />
    <title>Draw a rectangular shape</title>
</head>
<body onload="draw();">
    <canvas id="canvas" width="150" height="150"></canvas>
    <script src="./script.js"></script>
</body>
</html>
```
###### javascript
```javascript
function draw() {
  var canvas = document.getElementById('canvas');
  if (canvas.getContext) {
    var context = canvas.getContext('2d');

    context.fillRect(20,20,100,100);
    context.clearRect(40,40,60,60);
    context.strokeRect(45,45,50,50);
  }
}
```
#### Write a JavaScript program to draw a circle.  
###### html
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset=utf-8 />
    <title>Draw a circle</title>
</head>
<body onload="draw();">
    <canvas id="circle" width="150" height="150"></canvas>
    <script src="./script.js"></script>
</body>
</html>
```
###### javascript
```javascript
function draw() {
  var canvas = document.getElementById('circle');
  if (canvas.getContext) {
    var ctx = canvas.getContext('2d');
    var X = canvas.width / 2;
    var Y = canvas.height / 2;
    var R = 45;
    ctx.beginPath();
    ctx.arc(X, Y, R, 0, 2 * Math.PI, false);
    ctx.lineWidth = 3;
    ctx.strokeStyle = '#FF0000';
    ctx.stroke();
  }
}
```
#### . Write a JavaScript program to draw two intersecting rectangles, one of which has alpha transparency. 
###### html
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset=utf-8 />
    <title>Draw two intersecting rectangles, one of which has alpha transparency</title>
</head>
<body onload="draw();">
    <canvas id="canvas" width="150" height="150"></canvas>
    <script src="./script.js"></script>
</body>
</html>
```
###### javascript
```javascript
function draw() {
  var canvas = document.getElementById("canvas");
  if (canvas.getContext) {
    var context = canvas.getContext("2d");

    context.fillStyle = "rgb(256,0,0)";
    context.fillRect(15, 10, 55, 50);

    context.fillStyle = "rgba(0, 0, 200, 0.6)";
    context.fillRect(35, 30, 55, 50);
  }
}
```
#### Write a JavaScript program to draw the following right-angled triangle. 
###### javascript
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset=utf-8 />
    <title>Draw a right-angled triangle</title>
</head>
<body onload="draw();">
    <canvas id="canvas" width="150" height="150"></canvas>
    <script src="./script.js"></script>
</body>
</html>
```
###### javascript
```javascript
function draw() {
  var canvas = document.getElementById('canvas');
  if (canvas.getContext) {
    var context = canvas.getContext('2d');

    context.beginPath();
    context.moveTo(75, 75);
    context.lineTo(10, 75);
    context.lineTo(10, 25);
    context.fill();
  }
}
```
#### . Write a JavaScript program to draw the following diagram [use moveto() function]. 
#### html
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset=utf-8 />
    <title>Draw diagram using moveto() function</title>
</head>
<body onload="draw();">
    <canvas id="canvas" width="250" height="250"></canvas>
    <script src="./script.js"></script>
</body>
</html>
```
###### javascript
```javascript
function draw() 
{
  var canvas = document.getElementById('canvas');
  if (canvas.getContext)
  {
    var context = canvas.getContext('2d');
    context.beginPath();
    context.arc(75,75,50,0,Math.PI*2,true);
    context.moveTo(110,75);
    context.arc(75,75,35,0,Math.PI,false); 
    context.moveTo(55,65);
    context.arc(60,65,5,0,Math.PI*2,true); 
    context.arc(90,65,5,0,Math.PI*2,true);
    context.stroke();
  }
}
```
#### Write a JavaScript program to draw the following diagram [diagonal, white to black circles]. 
###### html
```html
<!DOCTYPE html>
<html>
<head>
    <title>Diagonal, White to Black circles</title>
</head>
<body>
    <canvas id="myCanvas" width="1500" height="800">
        <p>Update your browser!</p>
    </canvas>
    <script src="./script.js"></script>
</body>
</html>
```
###### javascript
```javascript
function draw() {
  var ctx = document.getElementById("myCanvas").getContext("2d");
  var counter = 0;
  for (var i = 0; i < 6; i++) {
    for (var j = 0; j < 6; j++) {
      //Start from white and goes to black
      ctx.fillStyle = "rgb(" + Math.floor(255 - 42.5 * i) + "," + Math.floor(255 - 42.5 * i) +
        "," + Math.floor(255 - 42.5 * j) + ")";
      ctx.beginPath();
      if (i === counter && j === counter) {
        //creates the circles
        ctx.arc(25 + j * 50, 30 + i * 50, 20, 0, Math.PI * 2, true);
        ctx.fill();
        //creates a border around the circles so white one will be vissible
        ctx.stroke();
      }
    }
    counter++;
  }
}
draw();
```
# JavaScript Object
#### Write a JavaScript program to list the properties of a JavaScript object.
```javascript
function keys(obj) 
 {
    if (!isObject(obj)) return [];
    if (Object.keys) return Object.keys(obj);
    var keys = [];
    for (var key in obj) if (has(obj, key)) keys.push(key);
    return keys;
  }
function isObject(obj) 
{
    var type = typeof obj;
    return type === 'function' || type === 'object' && !!obj;
  }
console.log(keys({red: "#FF0000", green: "#00FF00", white: "#FFFFFF"}));
```
#### Write a JavaScript program to delete the rollno property from the following object. Also print the object before or after deleting the property.  
```javascript
var student = {
  name: "David Rayy",
  sclass: "VI",
  rollno: 12
};
console.log(student);
delete student.rollno;
```
#### Write a JavaScript program to get the length of an JavaScript object. 
```javascript
Object.objsize = function (Myobj) {
  var osize = 0, key;
  for (key in Myobj) {
    if (Myobj.hasOwnProperty(key)) osize++;
  }
  return osize;
};

var student = {
  name: "David Rayy",
  sclass: "VI",
  rollno: 12
};
var objsize = Object.objsize(student);
console.log('Size of the current object : ' + objsize);
```
####  Write a JavaScript program to display the reading status (i.e. display book name, author name and reading status) of the following books. 
```javascript
var library = [
  {
    title: 'Bill Gates',
    author: 'The Road Ahead',
    readingStatus: true
  },
  {
    title: 'Steve Jobs',
    author: 'Walter Isaacson',
    readingStatus: true
  },
  {
    title: 'Mockingjay: The Final Book of The Hunger Games',
    author: 'Suzanne Collins',
    readingStatus: false
  }];

for (var i = 0; i < library.length; i++) {
  var book = "'" + library[i].title + "'" + ' by ' + library[i].author + ".";
  if (library[i].readingStatus) {
    console.log("Already read " + book);
  } else {
    console.log("You still need to read " + book);
  }
}
```
#### Write a JavaScript program to get the volume of a Cylinder with four decimal places using object classes. 
```javascript
function CylinderVolume(cyl_height, cyl_diameter) {
  this.cyl_height = cyl_height;
  this.cyl_diameter = cyl_diameter;
}
CylinderVolume.prototype.Volume = function () {
  var radius = this.cyl_diameter / 2;
  return this.cyl_height * Math.PI * radius * radius;
};
var cyl = new CylinderVolume(7, 4);
// Volume of the cylinder with four decimal places.
console.log('volume = ' + cyl.Volume().toFixed(4));
```
#### Write a Bubble Sort algorithm in JavaScript. 
```javascript
function bubbleSort(arr) {
  var is_sorted = false;
  while (!is_sorted) {
    is_sorted = true;
    for (var n = 0; n < arr.length - 1; n++) {
      if (arr[n] > arr[n + 1]) {
        var x = arr[n + 1];
        arr[n + 1] = arr[n];
        arr[n] = x;
        is_sorted = false;
      }
    }
  }
  return arr;
}
console.log(bubbleSort([6, 4, 0, 3, -2, 1]));
```
####  Write a JavaScript program which returns a subset of a string. 
```javascript
function subString(str) {
  var subset = [];
  for (var m = 0; m < str.length; m++) {
    for (var n = m + 1; n <= str.length; n++) {
      subset.push(str.slice(m, n));
    }
  }
  return subset;
}
console.log(subString("dog"));
```
#### Write a JavaScript program to create a Clock.   
```javascript
function clock() {
  this.cur_date = new Date();
  this.hours = this.cur_date.getHours();
  this.minutes = this.cur_date.getMinutes();
  this.seconds = this.cur_date.getSeconds();
}
clock.prototype.run = function () {
  setInterval(this.update.bind(this), 1000);
};
clock.prototype.update = function () {
  this.updateTime(1);
  console.log(this.hours + ":" + this.minutes + ":" + this.seconds);
};
clock.prototype.updateTime = function (secs) {
  this.seconds += secs;
  if (this.seconds >= 60) {
    this.minutes++;
    this.seconds = 0;
  }
  if (this.minutes >= 60) {
    this.hours++;
    this.minutes = 0;
  }
  if (this.hours >= 24) {
    this.hours = 0;
  }
};
var clock = new clock();
clock.run();
```
####  Write a JavaScript program to calculate the area and perimeter of a circle.  
```javascript
function areaOfCircle(radius) {
  this.radius = radius;
  this.area = function () {
    return Math.PI * this.radius * this.radius;
  };
  this.perimeter = function () {
    return 2 * Math.PI * this.radius;
  };
}
var c = new areaOfCircle(3);
console.log('Area =', c.area().toFixed(2));
console.log('perimeter =', c.perimeter().toFixed(2));
```
#### Write a JavaScript program to sort an array of JavaScript objects.   
```javascript
var library = [
  {
    title: 'Bill Gates',
    author: 'The Road Ahead',
    libraryID: 1254
  },
  {
    title: 'Steve Jobs',
    author: 'Walter Isaacson',
    libraryID: 4264
  },
  {
    title: 'Mockingjay: The Final Book of The Hunger Games',
    author: 'Suzanne Collins',
    libraryID: 3245
  }];

function sortObject (field_name, reverse, initial) {

  var key = initial ?
    function (x) {
      return initial(x[field_name]);
    } :
    function (x) {
      return x[field_name];
    };

  reverse = !reverse ? 1 : -1;

  return function (x, y) {
    return x = key(x), y = key(y), reverse * ((x > y) - (y > x));
  };
};

var newobj = library.sort(sortObject('libraryID', true, parseInt));
console.log(newobj);
```
#### Write a JavaScript function to print all the methods in an JavaScript object. 
```javascript
function FindAllMethods(obj) {
  return Object.getOwnPropertyNames(obj).filter(function (property) {
    return typeof obj[property] == "function";
  });
} 
console.log(FindAllMethods(Math));
console.log(FindAllMethods(Array));
function all_properties(obj) {
  return Object.getOwnPropertyNames(obj);
}
console.log(all_properties(Math));
console.log(all_properties(Array));
```
####  Write a JavaScript function to parse an URL.   
```javascript
function parseUrl(url) {
  var a = document.createElement('a');
  a.href = url;
  return {
      source: url,
      protocol: a.protocol.replace(':', ''),
      host: a.hostname,
      port: a.port,
      query: a.search,
      params: (function () {
          var ret = {},
              seg = a.search.replace(/^\?/, '').split('&'),
              len = seg.length,
              i = 0,
              s;
          for (; i < len; i++) {
              if (!seg[i]) {
                  continue;
              }
              s = seg[i].split('=');
              ret[s[0]] = s[1];
          }
          return ret;
      })(),
      file: (a.pathname.match(/\/([^\/?#]+)$/i) || [, ''])[1],
      hash: a.hash.replace('#', ''),
      path: a.pathname.replace(/^([^\/])/, '/$1'),
      relative: (a.href.match(/tps?:\/\/[^\/]+(.+)/) || [, ''])[1],
      segments: a.pathname.replace(/^\//, '').split('/')
  };
}
console.log(parseUrl('https://www.w3schools.com/js/js_intro.asp'));
```
# JavaScript validation  
#### Write a JavaScript function to validate whether a given value type is boolean or not. 
```javascript
function isBoolean(value) {
  return value === true || value === false || toString.call(value) === '[object Boolean]';
}
console.log(isBoolean(true));
console.log(isBoolean('bar'));
```
#### Write a JavaScript function to validate whether a given value type is error or not. 
```javascript
function isError(input) {
  return input instanceof Error || toString.call(input) === '[object Error]';
}
console.log(isError(new Error('foo')));
console.log(isError(100));
console.log(isError('foo'));
```
#### Write a JavaScript function to validate whether a given value type is NaN or not. 
```javascript
function isNaN(val) {
  return val !== val;
}
console.log(isNaN(NaN));
console.log(isNaN('bar'));
```
#### Write a JavaScript function to validate whether a given value type is null or not.   
```javascript
function is_null(val) {
  return val === null;
}
console.log(is_null(null));
console.log(is_null('bar'));
```
#### Write a JavaScript function to validate whether a given value is number or not.     
```javascript
function is_number(value) {
  return !isNaN(value) && toString.call(value) === '[object Number]';
}
console.log(is_number(NaN));
console.log(is_number(42.32));
console.log(is_number(72));
```
#### Write a JavaScript function to validate whether a given value is object or not.      
```javascript
function isObject(value) {
  var datatype = typeof value;
  return datatype === 'function' || datatype === 'object' && !!value;
}
console.log(isObject({ name: 'Robert' }));
console.log(isObject('bar'));
console.log(isObject(72));
```
####  Write a JavaScript function to validate whether a given value type is pure json object or not.      
```javascript
function isJson(value) {
  return toString.call(value) === '[object Object]';
}
console.log(isJson({ name: 'Robert' }));
console.log(isJson('bar'));
console.log(isJson(72));
```
#### Write a JavaScript function to validate whether a given value is RegExp or not.      
```javascript
function isRegularExp(value) {
  return toString.call(value) === '[object RegExp]';
}
console.log(isRegularExp(/test/));
console.log(isRegularExp('bar'));
console.log(isRegularExp(72));
```
#### Write a JavaScript function to validate whether a given value type is char or not.      
```javascript
function isChar(value) {
  if (Object.prototype.toString.call(value) !== '[object String]')
    return false;
  return value && value.length === 1;
}
console.log(isChar('f'));
console.log(isChar('hello'));
```
#### Write a JavaScript function to check whether given value types are same or not.       
```javascript
function isSameType(value1, value2) {
  if (isNaN(value1) || isNaN(value2)) {
    return isNaN(value1) === isNaN(value2);
  }
  return toString.call(value1) === toString.call(value2);
}
function isNaN(val) {
  return val !== val;
}
console.log(isSameType('12', 100));
console.log(isSameType('12', '100'));
console.log(isSameType(12, 100));
```
# Imp Questions
#### The Movie Database
1. Create an object to store the following information about your favorite movie: title (a 
string), duration (a number), and stars (an array of strings). 
2. Create a function to print out the movie information like so: "Puff the Magic Dragon lasts for 30 
minutes. Stars: Puff, Jackie, Living Sneezes."
```javascript
var favoriteMovie = {
  title: "Puff the Magic Dragon",
  duration: 30,
  stars: ["Puff", "Jackie", "Living Sneezes"]
};
function printMovieInfo(movie) {
  var starsList = movie.stars.join(", ");
  console.log(movie.title + " lasts for " + movie.duration + " minutes. Stars: " + starsList + ".");
}
printMovieInfo(favoriteMovie);
```
#### The Reading List
1. Create an array of objects, where each object describes a book and has properties for the title (a 
string), author (a string), and alreadyRead (a boolean indicating if you read it yet). 
2. Iterate through the array of books. For each book, log the book title and book author like so: "The 
Hobbit by J.R.R. Tolkien". 
3. Now use an if/else statement to change the output depending on whether you read it yet or not. If you 
read it, log a string like 'You already read "The Hobbit" by J.R.R. Tolkien', and if not, log a string like 
'You still need to read "The Lord of the Rings" by J.R.R. Tolkien.' 
```javascript
var library = [
  {
      title: "The Hobbit",
      author: "J.R.R. Tolkien",
      alreadyRead: true
  },
  {
      title: "The Lord of the Rings",
      author: "J.R.R. Tolkien",
      alreadyRead: false
  },
  {
      title: "Harry Potter and the Philosopher's Stone",
      author: "J.K. Rowling",
      alreadyRead: true
  }
];
for (var i = 0; i < library.length; i++) {
  var book = library[i];
  console.log(book.title + " by " + book.author);
  if (book.alreadyRead) {
      console.log('You already read "' + book.title + '" by ' + book.author + '.');
  } else {
      console.log('You still need to read "' + book.title + '" by ' + book.author + '.');
  }
} 
```
#### The Recipe Card
1. Create an object to hold information on your favorite recipe. It should have properties for title (a 
string), servings (a number), and ingredients (an array of strings). 
2. On separate lines (one console.log statement for each), log the recipe information so it looks like: 
 Mole 
 Serves: 2 
 Ingredients: 
 cinnamon 
 cumin 
 cocoa
```javascript
var favoriteRecipe = {
  title: "Mole",
  servings: 2,
  ingredients: ["cinnamon", "cumin", "cocoa"]
};
console.log(favoriteRecipe.title);
console.log("Serves: " + favoriteRecipe.servings);
console.log("Ingredients:");
for (var i = 0; i < favoriteRecipe.ingredients.length; i++) {
  console.log("- " + favoriteRecipe.ingredients[i]);
}
```
#### The Fortune Teller
Why pay a fortune teller when you can just program your fortune yourself? 
1. Write a function named tellFortune that: 
  1.1 takes 4 arguments: number of children, partner's name, geographic location, job title. 
  1.2 outputs your fortune to the screen like so: "You will be a X in Y, and married to Z with N kids." 
2. Call that function 3 times with 3 different values for the arguments.
```javascript
function tellFortune(numChildren, partnerName, geoLocation, jobTitle) {
  var fortune = "You will be a " + jobTitle + " in " + geoLocation + ", and married to " + partnerName + " with " + numChildren + " kids.";
  console.log(fortune);
}
tellFortune(2, "Alice", "New York", "Software Engineer");
tellFortune(3, "Bob", "London", "Graphic Designer");
tellFortune(1, "Charlie", "Paris", "Chef");
```
#### The Age Calculator
Forgot how old you are? Calculate it! 
1. Write a function named calculateAge that: 
   1.1 takes 2 arguments: birth year, current year. 
   1.2 calculates the 2 possible ages based on those years. 
   1.3 outputs the result to the screen like so: "You are either NN or NN" 
2. Call the function three times with different sets of values. 
3. Bonus: Figure out how to get the current year in JavaScript instead of passing it in.
```javascript
function calculateAge(birthYear, currentYear) {
  var age1 = currentYear - birthYear;
  var age2 = age1 - 1;
  console.log("You are either " + age2 + " or " + age1);
}
var currentYear = new Date().getFullYear();
calculateAge(1990, currentYear);
calculateAge(1985, currentYear);
calculateAge(2000, currentYear);
```
#### The Lifetime Supply Calculator 
Ever wonder how much a "lifetime supply" of your favorite snack is? Wonder no more! 
1. Write a function named calculateSupply that: 
   1.1 takes 2 arguments: age, amount per day. 
   1.2 calculates the amount consumed for rest of the life (based on a constant max age). 
   1.3 outputs the result to the screen like so: "You will need NN to last you until the ripe old age of X" 
2. Call that function three times, passing in different values each time. 
3. Bonus: Accept floating point values for amount per day, and round the result to a round number.
```javascript
function calculateSupply(currentAge, amountPerDay) {
  const maxAge = 100;
  const yearsRemaining = maxAge - currentAge;
  const amountPerYear = amountPerDay * 365.25; // Account for leap years
  const totalSupply = Math.round(yearsRemaining * amountPerYear);
  console.log("You will need " + totalSupply + " to last you until the ripe old age of " + maxAge);
}

// Call the function three times with different values
calculateSupply(25, 2.5);
calculateSupply(40, 3);
calculateSupply(60, 1.2);
```
#### The Geometrizer 
Create 2 functions that calculate properties of a circle, using the definitions here. 
Create a function called calcCircumfrence : 
Pass the radius to the function. 
Calculate the circumference based on the radius, and output "The circumference is NN". 
Create a function called calcArea : 
Pass the radius to the function. 
Calculate the area based on the radius, and output "The area is NN".
```javascript
function calcCircumference(radius) {
  var circumference = 2 * Math.PI * radius;
  console.log("The circumference is " + circumference.toFixed(2));
}
function calcArea(radius) {
  var area = Math.PI * Math.pow(radius, 2);
  console.log("The area is " + area.toFixed(2));
}

calcCircumference(5);
calcCircumference(10);
calcCircumference(15);
calcArea(5);
calcArea(10);
calcArea(15);
```
#### The Temperature Converter 
It's hot out! Let's make a converter based on the steps here. 
Create a function called celsiusToFahrenheit : 
Store a celsius temperature into a variable. 
Convert it to fahrenheit and output "NN°C is NN°F". 
Create a function called fahrenheitToCelsius : 
Now store a fahrenheit temperature into a variable. 
Convert it to celsius and output "NN°F is NN°C. 
```javascript
function celsiusToFahrenheit(celsius) {
  var fahrenheit = (celsius * 9/5) + 32;
  console.log(celsius + "°C is " + fahrenheit.toFixed(2) + "°F");
}

function fahrenheitToCelsius(fahrenheit) {
  var celsius = (fahrenheit - 32) * 5/9;
  console.log(fahrenheit + "°F is " + celsius.toFixed(2) + "°C");
}

celsiusToFahrenheit(0);
celsiusToFahrenheit(25);
celsiusToFahrenheit(100);
fahrenheitToCelsius(32);
fahrenheitToCelsius(77);
fahrenheitToCelsius(212);
```
# Other questions 
####  Create an HTML page. Add JavaScript that includes 2 prompts for integer values from the user. Add JavaScript to add these 2 values together and display the result in an alert box.  
```javascript
var num1 = prompt("Enter the first integer:");
var num2 = prompt("Enter the second integer:");
var int1 = parseInt(num1, 10);
var int2 = parseInt(num2, 10);
if (!isNaN(int1) && !isNaN(int2)) {
    var sum = int1 + int2;
    alert("The sum of " + int1 + " and " + int2 + " is " + sum + ".");
} else {
    alert("Please enter valid integers.");
}
```
####  Write a JavaScript function that returns a passed string with letters in alphabetical order.
```javascript
function alphabetizeString(str) {
  var charArray = str.split('');
  charArray.sort();
  var sortedStr = charArray.join('');
  return sortedStr;
}
console.log(alphabetizeString("javascript")); 
console.log(alphabetizeString("hello")); 
console.log(alphabetizeString("world"));
```
#### Write a JavaScript function to extract unique characters from a string 
“thequickbrownfoxjumpsoverthelazydog”. 
```javascript
function extractUniqueCharacters(str) {
  var uniqueChars = new Set();
  for (var i = 0; i < str.length; i++) {
      uniqueChars.add(str[i]);
  }
  var uniqueStr = Array.from(uniqueChars).join('');
  return uniqueStr;
}
console.log(extractUniqueCharacters("thequickbrownfoxjumpsoverthelazydog"));
```
#### Create an HTML page. Add a JavaScript function to convert local time and date to UTC and display the result. Add a button to your page that calls this function. Add JavaScript to create a timer that displays the current date and time after a specified amount of time delay. Use a button (or other event) to call the timer function 
###### html
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Local to UTC Time Converter and Timer</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            padding: 20px;
        }
        #currentTime, #utcTime, #delayedTime {
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <h1>Local to UTC Time Converter and Timer</h1>
    <button onclick="convertToUTC()">Convert Local Time to UTC</button>
    <div id="utcTime"></div>

    <button onclick="startTimer()">Start Timer</button>
    <div id="currentTime"></div>
    <div id="delayedTime"></div>

    <script src="script.js"></script>
</body>
</html>
```
###### javascript
```javascript
function convertToUTC() {
  var now = new Date();
  var utcString = now.toUTCString();
  document.getElementById('utcTime').innerText = 'Current UTC Time: ' + utcString;
}

function displayCurrentTime() {
  var now = new Date();
  document.getElementById('currentTime').innerText = 'Current Local Time: ' + now.toString();
}

function displayDelayedTime() {
  var now = new Date();
  document.getElementById('delayedTime').innerText = 'Delayed Local Time: ' + now.toString();
}

function startTimer() {
  var delay = 5000; 
  displayCurrentTime();
  setTimeout(displayDelayedTime, delay);
}
```
#### Create a basic page in html that consists of one image. Using the onClick event handler, when the user clicks on the image, change it to a unique image Reconfigure the previous question to execute using a function. Specifically, when the user clicks on the button, the onClick event handler calls a function. The function then executes the statement that changes the background color to blue. 
###### html
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Image Click and Background Change</title>
    <style>
        body {
            text-align: center;
            padding: 50px;
        }
        #changeColorButton {
            margin-top: 20px;
            padding: 10px 20px;
            font-size: 16px;
        }
    </style>
</head>
<body>
    <h1>Image Click and Background Change</h1>

    <img id="myImage" src="https://images.pexels.com/photos/1010640/pexels-photo-1010640.jpeg?auto=compress&cs=tinysrgb&w=600" alt="Initial Image" width="300" onclick="changeImage()">
    <br>
    <button id="changeColorButton" onclick="changeBackgroundColor()">Change Background Color</button>

    <script src="script.js"></script>
</body>
</html>
```
###### javascript
```javascript
function changeImage() {
  var image = document.getElementById('myImage');
  image.src = 'https://images.pexels.com/photos/163864/santorini-oia-greece-travel-163864.jpeg?auto=compress&cs=tinysrgb&w=600'; 
}

function changeBackgroundColor() {
  document.body.style.backgroundColor = 'blue';
}
```
#### Create an HTML page that includes 2 paragraphs of text. Add JavaScript to insert a new paragraph in between the other 2. Add JavaScript to use an event to change the style of the new paragraph using either the style property or the className property. Add JavaScript to use an event to change the style of the new paragraph back to the original. 
###### html
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Insert and Style Paragraph</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            padding: 20px;
        }
        .styled {
            color: blue;
            font-weight: bold;
        }
        .original {
            color: black;
            font-weight: normal;
        }
    </style>
</head>
<body>
    <p id="para1">This is the first paragraph.</p>
    <p id="para2">This is the second paragraph.</p>
    
    <button onclick="insertParagraph()">Insert Paragraph</button>
    <button onclick="styleParagraph()">Style Paragraph</button>
    <button onclick="revertStyle()">Revert Style</button>

    <script src="script.js"></script>
</body>
</html>
```
###### javascript
```javascript
function insertParagraph() {
  var newPara = document.createElement('p');
  newPara.id = 'newPara';
  newPara.className = 'original';
  newPara.textContent = 'This is the new paragraph inserted between the first and second paragraphs.';
  
  var para1 = document.getElementById('para1');
  var para2 = document.getElementById('para2');
  document.body.insertBefore(newPara, para2);
}

function styleParagraph() {
  var newPara = document.getElementById('newPara');
  if (newPara) {
      newPara.className = 'styled';
  } else {
      alert('Please insert the new paragraph first.');
  }
}

function revertStyle() {
  var newPara = document.getElementById('newPara');
  if (newPara) {
      newPara.className = 'original';
  } else {
      alert('Please insert the new paragraph first.');
  }
}
```
#### Create a slide show of 5 images.  
###### html
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Slideshow Example</title>
</head>
<style>
.slideshow-container {
    max-width: 600px;
    position: relative;
    margin: auto;
    overflow: hidden;
}
.mySlides {
    display: none;
    width: 100%;
}
.fade {
    animation-name: fade;
    animation-duration: 1.5s;
}
@keyframes fade {
    from {opacity: .4}
    to {opacity: 1}
}
</style>
<body>
<div class="slideshow-container">
    <div class="mySlides fade">
        <img src="https://images.pexels.com/photos/4817608/pexels-photo-4817608.png?auto=compress&cs=tinysrgb&w=600" style="width:100%">
    </div>

    <div class="mySlides fade">
        <img src="https://images.pexels.com/photos/1285625/pexels-photo-1285625.jpeg?auto=compress&cs=tinysrgb&w=600" style="width:100%">
    </div>

    <div class="mySlides fade">
        <img src="https://images.pexels.com/photos/164041/pexels-photo-164041.jpeg?auto=compress&cs=tinysrgb&w=600" style="width:100%">
    </div>

    <div class="mySlides fade">
        <img src="https://images.pexels.com/photos/164336/pexels-photo-164336.jpeg?auto=compress&cs=tinysrgb&w=600" style="width:100%">
    </div>

    <div class="mySlides fade">
        <img src="https://images.pexels.com/photos/163864/santorini-oia-greece-travel-163864.jpeg?auto=compress&cs=tinysrgb&w=600" style="width:100%">
    </div>
</div>
<script src="script.js"></script> 
</body>
</html>
```
###### javascript
```javascript
var slideIndex = 0;
showSlides();

function showSlides() {
    var slides = document.getElementsByClassName("mySlides");
    for (var i = 0; i < slides.length; i++) {
        slides[i].style.display = "none";
    }
    slideIndex++;
    if (slideIndex > slides.length) {
        slideIndex = 1;
    }
    slides[slideIndex - 1].style.display = "block";
    setTimeout(showSlides, 2000); // Change image every 2 seconds
}
```
#### Use previous question images and add two image button (back and forward). Back button allows the user to move backward through the slide show one slide at a time. When the user reaches the end (or beginning when clicking on the back button) of the slide show, the slide show should not wrap around to the beginning (or end) and forward button should show next image. When at the beginning of the slide show, only the forward image button should be visible. Conversely, when at the end, only the back image button should be visible. 
###### html
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Slideshow Example</title>
</head>
<style>
    .slideshow-container {
    max-width: 600px;
    position: relative;
    margin: auto;
    overflow: hidden;
}

.mySlides {
    display: none;
    width: 100%;
}

.fade {
    animation-name: fade;
    animation-duration: 1.5s;
}

@keyframes fade {
    from {opacity: .4}
    to {opacity: 1}
}
</style>
<body>
<div class="slideshow-container">
    <div class="mySlides fade">
        <img src="https://images.pexels.com/photos/4817608/pexels-photo-4817608.png?auto=compress&cs=tinysrgb&w=600" style="width:100%">
    </div>

    <div class="mySlides fade">
        <img src="https://images.pexels.com/photos/1285625/pexels-photo-1285625.jpeg?auto=compress&cs=tinysrgb&w=600" style="width:100%">
    </div>

    <div class="mySlides fade">
        <img src="https://images.pexels.com/photos/164041/pexels-photo-164041.jpeg?auto=compress&cs=tinysrgb&w=600" style="width:100%">
    </div>

    <div class="mySlides fade">
        <img src="https://images.pexels.com/photos/164336/pexels-photo-164336.jpeg?auto=compress&cs=tinysrgb&w=600" style="width:100%">
    </div>

    <div class="mySlides fade">
        <img src="https://images.pexels.com/photos/163864/santorini-oia-greece-travel-163864.jpeg?auto=compress&cs=tinysrgb&w=600" style="width:100%">
    </div>
    <!-- Navigation buttons -->
    <button id="backBtn" onclick="plusSlides(-1)" style="display:none">&#10094; Back</button>
    <button id="forwardBtn" onclick="plusSlides(1)">Forward &#10095;</button>
</div>
<script src="script.js"></script> 
</body>
</html>
```
###### javascript
```javascript
var slideIndex = 1;
showSlides(slideIndex);

function plusSlides(n) {
    showSlides(slideIndex += n);
}

function showSlides(n) {
    var slides = document.getElementsByClassName("mySlides");
    var backBtn = document.getElementById("backBtn");
    var forwardBtn = document.getElementById("forwardBtn");
    if (n > slides.length) {
        slideIndex = slides.length;
    }
    if (n < 1) {
        slideIndex = 1;
    }

    for (var i = 0; i < slides.length; i++) {
        slides[i].style.display = "none";
    }
    slides[slideIndex - 1].style.display = "block";
    if (slideIndex === 1) {
        backBtn.style.display = "none";
        forwardBtn.style.display = "block";
    } else if (slideIndex === slides.length) {
        backBtn.style.display = "block";
        forwardBtn.style.display = "none";
    } else {
        backBtn.style.display = "block";
        forwardBtn.style.display = "block";
    }
}
```
#### Create a basic page. Using the setTimeout() method, create an animation on the page. Allow the user to stop the animation by placing the cursor on any marble. Allow the user to restart the animation by removing the cursor from that marble. 
###### html
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Animation Example</title>
    <style>
        .marble {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background-color: #3498db;
            position: absolute;
            animation: move 2s linear infinite;
        }
        @keyframes move {
            0% { top: 0; left: 0; }
            50% { top: 100px; left: 100px; }
            100% { top: 0; left: 0; }
        }
    </style>
</head>
<body>
    <div class="marble" id="marble1"></div>
    <div class="marble" id="marble2"></div>
    <div class="marble" id="marble3"></div>

    <script src="script.js"></script> 
</body>
</html>
```
###### javascript
```javascript
function stopAnimation() {
  var marbles = document.querySelectorAll('.marble');
  marbles.forEach(function(marble) {
      marble.style.animationPlayState = 'paused';
  });
}
function restartAnimation() {
  var marbles = document.querySelectorAll('.marble');
  marbles.forEach(function(marble) {
      marble.style.animationPlayState = 'running';
  });
}
document.querySelectorAll('.marble').forEach(function(marble) {
  marble.addEventListener('mouseover', stopAnimation);
  marble.addEventListener('mouseout', restartAnimation);
});
```
#### Create a basic page in html. Then, display the following items in the page using only one or more document.write() statements: 
1. Information about the web browser that the user is viewing this page 
with. 
2. The height and width of the user's monitor, i.e. the resolution 
3. The date that the page was created or last modified.
###### html
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Basic Page</title>
</head>
<body>
    <h1>Basic Page</h1>
    <div id="browserInfo"></div>
    <div id="monitorResolution"></div>
    <div id="pageDate"></div>
    
    <script src="script.js" defer></script> 
</body>
</html>
```
###### javascript
```javascript
function displayBrowserInfo() {
  var browserInfo = document.getElementById('browserInfo');
  browserInfo.innerHTML = "<h2>Browser Information:</h2>" +
    "<p>User Agent: " + navigator.userAgent + "</p>" +
    "<p>Browser Version: " + navigator.appVersion + "</p>" +
    "<hr>";
}
function displayMonitorResolution() {
  var monitorResolution = document.getElementById('monitorResolution');
  monitorResolution.innerHTML = "<h2>Monitor Resolution:</h2>" +
    "<p>Width: " + screen.width + " pixels</p>" +
    "<p>Height: " + screen.height + " pixels</p>" +
    "<hr>";
}
function displayPageDate() {
  var pageDate = document.getElementById('pageDate');
  var lastModified = new Date(document.lastModified);
  pageDate.innerHTML = "<h2>Page Date Information:</h2>" +
    "<p>Last Modified: " + lastModified.toLocaleString() + "</p>" +
    "<hr>";
}

displayBrowserInfo();
displayMonitorResolution();
displayPageDate();
```
#### Create a basic page in html that displays 2 images. When the user places a cursor over any image, replace the image with a different image. When the user removes the cursor from the image and return it to its original state. 
###### html
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Image Switch</title>
    <style>
        .image {
            width: 300px;
            height: auto;
        }
    </style>
</head>
<body>
    <h1>Image Switch Example</h1>
    <img id="image1" class="image" src="original_image1.jpg" onmouseover="changeImage(this)" onmouseout="restoreImage(this)">
    <img id="image2" class="image" src="original_image2.jpg" onmouseover="changeImage(this)" onmouseout="restoreImage(this)">

    <script src="script.js"></script> 
</body>
</html>
```
###### javascript
```javascript
function changeImage(img) {
  if (img.id === 'image1') {
      img.src = 'https://images.pexels.com/photos/347141/pexels-photo-347141.jpeg?auto=compress&cs=tinysrgb&w=600'; 
  } else if (img.id === 'image2') {
      img.src = 'https://images.pexels.com/photos/163864/santorini-oia-greece-travel-163864.jpeg?auto=compress&cs=tinysrgb&w=600'; 
  }
}
function restoreImage(img) {
  if (img.id === 'image1') {
      img.src = 'https://images.pexels.com/photos/1029021/pexels-photo-1029021.jpeg?auto=compress&cs=tinysrgb&w=600'; 
  } else if (img.id === 'image2') {
      img.src = 'https://images.pexels.com/photos/161275/santorini-travel-holidays-vacation-161275.jpeg?auto=compress&cs=tinysrgb&w=600'; 
  }
}
```
#### Create a signup form with validation before submit 
###### html
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Signup Form with Validation</title>
    <style>
        .error {
            color: red;
        }
    </style>
</head>
<body>
    <h1>Signup Form</h1>
    <form id="signupForm" onsubmit="return validateForm()">
        <label for="username">Username:</label><br>
        <input type="text" id="username" name="username" required><br>
        <span id="usernameError" class="error"></span><br>

        <label for="email">Email:</label><br>
        <input type="email" id="email" name="email" required><br>
        <span id="emailError" class="error"></span><br>

        <label for="password">Password:</label><br>
        <input type="password" id="password" name="password" required><br>
        <span id="passwordError" class="error"></span><br>

        <label for="confirmPassword">Confirm Password:</label><br>
        <input type="password" id="confirmPassword" name="confirmPassword" required><br>
        <span id="confirmPasswordError" class="error"></span><br>

        <input type="submit" value="Sign Up">
    </form>

    <script src="script.js"></script> 
</body>
</html>
```
###### javascript
```javascript
function validateForm() {
  var username = document.getElementById('username').value.trim();
  var email = document.getElementById('email').value.trim();
  var password = document.getElementById('password').value;
  var confirmPassword = document.getElementById('confirmPassword').value;

  document.getElementById('usernameError').textContent = '';
  document.getElementById('emailError').textContent = '';
  document.getElementById('passwordError').textContent = '';
  document.getElementById('confirmPasswordError').textContent = '';

  var isValid = true;

  if (username.length < 3 || username.length > 20) {
      document.getElementById('usernameError').textContent = 'Username must be between 3 and 20 characters';
      isValid = false;
  }
  if (!validateEmail(email)) {
      document.getElementById('emailError').textContent = 'Invalid email format';
      isValid = false;
  }
  if (password.length < 6) {
      document.getElementById('passwordError').textContent = 'Password must be at least 6 characters';
      isValid = false;
  }
  if (password !== confirmPassword) {
      document.getElementById('confirmPasswordError').textContent = 'Passwords do not match';
      isValid = false;
  }
  return isValid;
}
function validateEmail(email) {
  var re = /\S+@\S+\.\S+/;
  return re.test(email);
}
```
#### Create a basic page in html that displays text and an image. Track how many times a user has visited your page by storing this information in a cookie. Display this information to the user, e.g. You have visited x number of times! The current visit should be included in this number. Display the date and time of the user's last visit, e.g. "You lasted visted on..." If this is the user's first visit, display e.g. "You have never visited before" instead. 
###### html
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Visit Tracker</title>
</head>
<body>
    <h1>Welcome to Visit Tracker Page</h1>
    <p id="visitInfo"></p>
    <p id="lastVisitedInfo"></p>
    <img src="https://images.pexels.com/photos/161275/santorini-travel-holidays-vacation-161275.jpeg?auto=compress&cs=tinysrgb&w=600" alt="Example Image" width="300">
</body>
<script src="script.js"></script> 
</html>
```
###### javascript
```javascript
function setCookie(cookieName, cookieValue, expiryDays) {
  var d = new Date();
  d.setTime(d.getTime() + (expiryDays * 24 * 60 * 60 * 1000));
  var expires = "expires=" + d.toUTCString();
  document.cookie = cookieName + "=" + cookieValue + ";" + expires + ";path=/";
}

function getCookie(cookieName) {
  var name = cookieName + "=";
  var decodedCookie = decodeURIComponent(document.cookie);
  var cookieArray = decodedCookie.split(';');
  for (var i = 0; i < cookieArray.length; i++) {
    var cookie = cookieArray[i].trim();
    if (cookie.indexOf(name) == 0) {
      return cookie.substring(name.length, cookie.length);
    }
  }
  return "";
}

function displayVisitInfo() {
  var visitCount = getCookie("visitCount");
  var lastVisited = getCookie("lastVisited");

  if (visitCount === "") {
    visitCount = 1;
    setCookie("visitCount", visitCount, 30);
    document.getElementById("visitInfo").textContent = "You have visited 1 time!";
    document.getElementById("lastVisitedInfo").textContent = "This is your first visit.";
  } else {
    visitCount = parseInt(visitCount) + 1;
    setCookie("visitCount", visitCount, 30);
    document.getElementById("visitInfo").textContent = "You have visited " + visitCount + " times!";
    if (lastVisited !== "") {
      document.getElementById("lastVisitedInfo").textContent = "You last visited on " + lastVisited;
    } else {
      document.getElementById("lastVisitedInfo").textContent = "Welcome back! It seems this is your first time.";
    }
  }

  var currentDate = new Date().toUTCString();
  setCookie("lastVisited", currentDate, 30);
}
displayVisitInfo();
```
#### Create a "Mad-libs" game using JavaScript.  Create a blank page. Using a prompt box, prompt the user to supply his or her name. Then, using 5 additional prompt boxes, prompt the user to supply 5 words. Save each word in a separate variable. Then, using document.write() statements, use the information stored in variables to display a "Mad-libs" type of story, i.e. create a few paragraphs of information in story format. Also, prompt the user for a color (i.e. one of the 16 named colors or a hex value). Store this color in a variable. In the "mad libs" story, highlight, using the color supplied by the user, each of the words that you previously collected. Do this by surrounding the words with <div> tags and using an inline style.
###### javascript
```javascript
var userName = prompt("Enter your name:");
var word1 = prompt("Enter a noun:");
var word2 = prompt("Enter an adjective:");
var word3 = prompt("Enter another noun:");
var word4 = prompt("Enter a verb:");
var word5 = prompt("Enter a place:");

var userColor = prompt("Choose a color (name or hex value):");

document.write("<h2>Mad Libs Story</h2>");
document.write("<p>Once upon a time, <div style='color: " + userColor + "; display: inline'>" + userName + "</div> found a magical <div style='color: " + userColor + "; display: inline'>" + word1 + "</div> in a <div style='color: " + userColor + "; display: inline'>" + word2 + "</div> forest. Excitedly, <div style='color: " + userColor + "; display: inline'>" + userName + "</div> picked up the <div style='color: " + userColor + "; display: inline'>" + word1 + "</div> and decided to take it to <div style='color: " + userColor + "; display: inline'>" + word3 + "</div>.</p>");
document.write("<p>On the way, they encountered a friendly <div style='color: " + userColor + "; display: inline'>" + word4 + "</div> who offered to help them find their way. Together, they journeyed through the <div style='color: " + userColor + "; display: inline'>" + word5 + "</div> and finally reached their destination.</p>");
document.write("<p>And so, <div style='color: " + userColor + "; display: inline'>" + userName + "</div> and their new <div style='color: " + userColor + "; display: inline'>" + word1 + "</div> lived happily ever after in the <div style='color: " + userColor + "; display: inline'>" + word2 + "</div> forest.</p>");
```
