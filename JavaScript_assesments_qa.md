# JavaScript Basis

#### Write a JavaScript program to display the current day and time in the following format.
#### Sample Output : Today is : Friday.
#### Current time is : 4 PM : 50 : 22

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

#### Write a JavaScript program to print the contents of the current window

<!DOCTYPE html>
<html>
<head>
    <title>Welcome To My Website</title>
</head>
<body>
    <h5>Welcome to My Website</h5>
    <p>This is a sample content that will be printed.</p>
    <button onclick="printWindow()">Print this page</button>

    <script>
        function printWindow() {
            window.print();
        }
    </script>
</body>
</html>

#### Write a JavaScript program to get the current date.
Expected Output :
mm-dd-yyyy, mm/dd/yyyy or dd-mm-yyyy, dd/mm/yyyy

const now = new Date();
const day = String(now.getDay()).padStart(2, '0');
const month = String(now.getMonth() + 1).padStart(2, '0');
const year = now.getFullYear();

document.write("mm-dd-yyyy : " + month + '-' + day + '-' + year + '<br>');
document.write("mm/dd/yyyy : " + month + '/' + day + '/' + year + '<br>');
document.write("dd-mm-yyyy : " + day + '-' + month + '-' + year + '<br>');
document.write("dd/mm/yyyy : " + day + '/' + month + '/' + year);

#### Write a JavaScript program to find the area of a triangle where lengths of the
three of its sides are 5, 6, 7.

const a = 5;
const b = 6;
const c = 7;

//calculate the semi perimeter
const s = a + b + c / 2;

//calculate the area
const area = Math.sqrt(s * (s - a) * (s - b) * (s - c));

document.write("Area of triangle is : " + area

#### Write a JavaScript program to rotate the string 'w3resource' in right direction by periodically 
removing one letter from the end of the string and attaching it to the front.

let str = 'w3resource'; 
function rotateString() { 
str = str[str.length - 1] + str.substring(0, str.length - 1); 
console.log(str); 
} 
// Rotate the string every 500 milliseconds 
setInterval(rotateString, 500);

#### Write a JavaScript program to determine whether a given year is a leap year in
the Gregorian calendar.

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

#### Write a JavaScript program to find 1st January be a Sunday between 2014 and 2050.

function firstJanSunday () {
    for(let year = 2014; year <= 2050; year++){
        const date = new Date(year, 0, 1);
        if(date.getDay() === 0){
            document.write("January 1st " + year + "is a Sunday" + "<br>" )
        }
    }
}firstJanSunday();

#### Write a JavaScript program where the program takes a random integer between 1 to 10, the user is then prompted to input a guess number. If the user input matches with guess number, the program will display a message "Good Work" otherwise display a message "Not matched".

<!-- Generate a random number between 1 and 10 -->
const randomNumber = Math.floor(Math.random() * 10) + 1;

<!-- User promt to guess a number -->
const userGuess = prompt("Guess a number between 1 and 10:");

<!-- convert user input to string -->
const guessNumber = parseInt(userGuess);

#### Write a JavaScript program to calculate days left until next Christmas.

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


// Check if user's guess matches the random number
if (guessNumber === randomNumber) {
    document.write("Good Work!");
} else {
    document.write("Not matched. The correct number was " + randomNumber + ".");
}

#### Write a JavaScript program to calculate multiplication and division of two numbers (input from user).

// javascript program to calculate multiplication and division
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

    <script>
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
    </script>
</body>
</html>

#### Write a JavaScript program to convert temperatures to and from celsius, fahrenheit. [ Formula : c/5 = (f-32)/9 [ where c = temperature in celsius and f = temperature in fahrenheit ] 
##### Expected Output : 60°C is 140 °F 45°F is 7.222222222222222°C

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

#### Write a JavaScript program to get the website URL (loading page).

// Get the current URL
const currentURL = window.location.href;

// Output the current URL
document.write("The current URL is: " + currentURL);

# JavaScripr Function

#### Write a JavaScript function that reverse a number. 
Example x = 32243; 
Expected Output : 34223

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

#### Write a JavaScript function that checks whether a passed string is palindrome or not? A palindrome is word, phrase, or sequence that reads the same backward as forward, e.g., madam or nurses run.

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

#### Write a JavaScript function that generates all combinations of a string. 
Example string : 'dog'
Expected Output : d,do,dog,o,og,g

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

// Example usage
const testStr = 'dog';
const result = generateCombinations(testStr);
document.write(result.join(','));

#### Write a JavaScript function that returns a passed string with letters in alphabetical order. Example string : 'webmaster' 
Expected Output : 'abeemrstw' 
Assume punctuation and numbers symbols are not included in the passed string.

function sortStringAlphabetically(str) {
    // Convert the string to an array of characters
    let charArray = str.split('').sort().join('');
    
    return charArray;
}

// Example usage
const exampleStr = 'webmaster';
const charArray = sortStringAlphabetically(exampleStr);
document.write(`Original string: ${exampleStr}`);
document.write(`Sorted string: ${charArray}`);

#### Write a JavaScript function that accepts a string as a parameter and converts the first letter of each word of the string in upper case. 
Example string : 'the quick brown fox' 
Expected Output : 'The Quick Brown Fox '

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

// Example usage
const exampleStr = 'the quick brown fox';
const capitalizedStr = capitalizeWords(exampleStr);
console.log(capitalizedStr); // Output: 'The Quick Brown Fox'

#### Write a JavaScript function that accepts a string as a parameter and find the longest word within the string. 
Example string : 'Web Development Tutorial' 
Expected Output : 'Development'

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

// Example usage
const exampleStr = 'Web Development Tutorial';
const longestWord = findLongestWord(exampleStr);
document.write(`Longest word in "${exampleStr}" is "${longestWord}"`);

#### Write a JavaScript function that accepts a string as a parameter and counts the number of vowels within the string. 
Note : As the letter 'y' can be regarded as both a vowel and a consonant, we do not count 'y' as vowel here. 
Example string : 'The quick brown fox' 
Expected Output : 5

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

// Example usage
const exampleStr = 'The quick brown fox';
const vowelCount = countVowels(exampleStr);

// Output using document.write
document.write(`Number of vowels in "${exampleStr}": ${vowelCount}`);
