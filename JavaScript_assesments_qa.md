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
