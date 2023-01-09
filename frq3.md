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

function calculate(expression) {
    result = document.getElementById("result");
    fetch('https://samayascsa.tk/api/calculator/' + expression)
    .then(response => response.json())
    .then(data => {
        console.log(data);
        result.innerHTML = expression + " = " + data.Result;
    })
}

</script>