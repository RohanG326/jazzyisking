## FRQ 1
<p id="test"></p>





<script>

function numberOfLeapYears(year1, year2) {
    
    result = document.getElementById("numberOfLeapYearsResult");

    // Fetch data from API
    fetch('https://samayascsa.tk/api/calendar/numberOfLeapYears/' + year1 + "/" + year2)
    .then(response => response.json())
    .then(data => {

        console.log(data);

        result.innerHTML = "Leap Years between " + year1 + "and " + year2 + ": " + data.numberOfLeapYears;

    })
}

function getYear1(){
    let inputYear1 = document.getElementById("inputYear1").value;
    return inputYear1;
}

function getYear2(){
    let inputYear2 = document.getElementById("inputYear2").value;
    return inputYear2;
}

function getYear(){
    let inputYear = document.getElementById("inputYear").value;
    return inputYear;
}


function isLeapYear(yearparam) {
    
    result = document.getElementById("isLeapYearResult");

    // Fetch data from API
    fetch('https://samayacsa.tk/api/calendar/isLeapYear/' + yearparam)
    .then(response => response.json())
    .then(data => {

        console.log(data);

        result.innerHTML = data.isLeapYear;

    })
}

</script>

### Check if a Year is a Leap Year
<input id="inputYear" placeholder="Input a Year">
<button onclick="isLeapYear(getYear())">Submit</button>
<p id="isLeapYearResult"></p>

### Check the Number of Leap Years in an Interval
<input id="inputYear1" placeholder="Input Starting Year">
    <input id="inputYear2" placeholder="Input Ending Year">
    <button onclick="numberOfLeapYears(getYear1(), getYear2())">Submit</button>
<p id="numberOfLeapYearsResult"></p>
