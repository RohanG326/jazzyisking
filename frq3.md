## FRQ 3

<input id="input" placeholder="Input equation">
    <button onclick="calculate(getInput())">Calculate</button>

<h2 id="result"></h2>

<script>

function getInput(){
    let equation = document.getElementById("input").value;
    console.log(equation);
    return equation;
}

function calculate(phrase) {
    result = document.getElementById("result");
    fetch('https://samayacsa.tk/api/calculator/' + phrase)
    .then(response => response.json())
    .then(data => {
        console.log(data);
        result.innerHTML = data.Result;
    })
}

</script>
