## Calendar FRQ

<script>

function getYear(){
    let inputYear = document.getElementById("inputYear").value;
    return inputYear;
}

function getMonth(){
    let inputMonth = document.getElementById("inputMonth").value;
    return inputMonth;
}

function getDay(){
    let inputDay = document.getElementById("inputDay").value;
    return inputDay;
}

function getYear2(){
    let inputYear2 = document.getElementById("inputYear2").value;
    return inputYear2;
}

function isLeapYear(yearParam) {
    
    result = document.getElementById("isLeapYearResult");

    // Fetch data from API
    fetch('https://serafina.tk/api/calendar/isLeapYear/' + yearParam)
    .then(response => response.json())
    .then(data => {

        console.log(data);

        result.innerHTML = "Is " + yearParam + " a leap year: " + data.isLeapYear;

    })
}

function firstDayOfYear(yearParam) {

    result = document.getElementById("theFirstDayOfYear");
    fetch('https://serafina.tk/api/calendar/firstDayOfYear/' + yearParam)
    .then(response => response.json())
    .then(data => {
        
        console.log(data);

        result.innerHTML = "The first day of the year " + yearParam + " was this day of the week: " + data.firstDayOfYear;
    })
}

function dayOfYear(monthParam, dayParam, yearParam) {
    
    result = document.getElementById("dayOfYear");
    valueParam = monthParam + '/' + dayParam + '/' + yearParam;
    // Fetch data from API
    fetch('https://serafina.tk/api/calendar/dayOfYear/' + valueParam)
    .then(response => response.json())
    .then(data => {

        console.log(data);

        result.innerHTML = "What day of the year is the date " + monthParam+ "/"+ dayParam+ "/"+ yearParam+ "?  "  + data.dayOfYear;

    })
}

function numberOfLeapYears(yearParam, year2Param) {
    
    result = document.getElementById("numberOfLeapYears");

    // Fetch data from API
    fetch('https://serafina.tk/api/calendar/numberOfLeapYears/' + yearParam+ '/' +year2Param)
    .then(response => response.json())
    .then(data => {

        console.log(data);

        result.innerHTML = "How many leap years are between " + yearParam + " and " +year2Param +"? " +data.numberOfLeapYears;

    })
}


function dayOfWeek(monthParam,dayParam, yearParam) {
    
    result = document.getElementById("dayOfWeek");
    valueParam = monthParam + '/' + dayParam + '/' + yearParam;
    
    // Fetch data from API
    fetch('https://serafina.tk/api/calendar/dayOfWeek/' +valueParam)
    .then(response => response.json())
    .then(data => {

        console.log(data);

        result.innerHTML = "What day of the week is the date " + monthParam+ "/"+ dayParam+ "/"+ yearParam+ "?  "+ data.dayOfWeek;

    })
}
</script>

<input id="inputYear" placeholder="Input a Year">
### Is this year a leap year?
<button onclick="isLeapYear(getYear())">Submit</button>
<p id="isLeapYearResult"></p>

### The day of week of the first day of Year 
<button onclick="firstDayOfYear(getYear())">Submit</button>
<p id="theFirstDayOfYear"></p>

### Number of leap years between years
<input id="inputYear2" placeholder="Input a second Year">
<button onclick="numberOfLeapYears(getYear(),getYear2())">Submit</button>
<p id="numberOfLeapYears"></p>

<input id="inputMonth" placeholder="Input a month">
<input id="inputDay" placeholder="Input a day">
### Day of Year
<button onclick="dayOfYear(getMonth(),getDay(), getYear())">Submit</button>
<p id="dayOfYear"></p>


### Day of week
<button onclick="dayOfWeek(getMonth(),getDay(), getYear())">Submit</button>
<p id="dayOfWeek"></p>

<style> 


p {
  font-size: 20px;
  color: white;
}
</style>