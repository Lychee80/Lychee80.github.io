## Calculator FRQ 

### You can use this feature to do some basic calculations :)


<script>

function calculate(){
    var expression = document.getElementById("expression").value;

    var str_url_expression = "https://serafina.tk/api/calculator/" + expression;
    console.log(str_url_expression)

    fetch(str_url_expression)
    // response is a RESTful "promise" on any successful fetch
    .then(response => {
      // check for response errors
    if (response.status !== 200) {
        error('GET API/Fetch Response Failure: ' + response.status);
        return;
    }
    
    // valid response will have JSON data
    response.text().then(data => {
        console.log(data);
        document.getElementById("calculated_result").innerHTML = "Result: " + data;
    })
})

}

</script>

<style> 
button {
background-color: pink;
  border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  cursor: pointer;
  border-radius: 12px;
}

p {
  font-size: 20px;
  color: white;
}
</style>

<br>
<h2>Calculate: </h2>
<label for="expression">Enter Expression: </label>
<input type="text" id="expression" name="expression" >
<br>
<br>
<button onclick="calculate()">Calculate Now!</button> 
<br>
<h3 id="calculated_result">The answer is: </h3>
<br>
<br>