## FRQ4

<script>

function getRows(){
    let inputRow = document.getElementById("inputRow").value;
    return inputRow;
}

function getColumns(){
    let inputColumn = document.getElementById("inputColumn").value;
    return inputColumn;
}

function getRGB(red, green, blue)
{
        console.log("rgb: " + red);
        return ( "#" + red.toString(16) + green.toString(16) + blue.toString(16));    
}

function generate(rowsparam, columnparam) {
    console.log("button clicked");
    fetch("https://serafina.tk/api/lightboard/" + rowsparam+ "/" + columnparam, {"method": "GET"})
    // response is a RESTful "promise" on any successful fetch
    .then(response => {
        // check for response errors
        if (response.status !== 200) {
            error("GET API response failure: " + response.status)
            return;  // api failure
        }
        // valid response will have JSON data
        response.json().then(data => {

        console.log(data);
        //clear previous results
        document.getElementById("result").innerHTML = "";
        var board = data;

        var table = document.createElement("table");
        table.setAttribute("border", "1");
        table.setAttribute("style", "border-collapse: collapse;");
        var tableBody = document.createElement("tbody");       

        for (var i = 0; i < board.length; i++) {
            var row = document.createElement("tr");
            for (var j = 0; j < columnparam; j++) {
            var cell = document.createElement("td");
            var cellText = document.createTextNode(board[i].light.effect);
            var cellText2 = document.createTextNode(getRGB(board[i].light.red, board[i].light.green, board[i].light.blue));
            // set color of cell based on rgb hex code if light is on
            if (!board[i].light.on) {
                cell.setAttribute("style", "background-color: " + getRGB(board[i].light.red, board[i].light.green, board[i].light.blue));
            }
            cell.appendChild(cellText);
            cell.appendChild(cellText2);
            row.appendChild(cell);
            i++;
            }
            i--;
            tableBody.appendChild(row);
        }
        table.appendChild(tableBody);        

        document.getElementById("result").appendChild(table);
        })
        // catch fetch errors
        .catch(err => {
            error(err + " " );
        });
    })
}

</script>

### Click to generate new lightboard!

<input id="inputRow" placeholder="Input number of Rows">
<input id="inputColumn" placeholder="Input number of Columns">
<button onclick="generate(getRows(), getColumns())">Generate</button>
<div id="result"></div>

<style> 

p {
  font-size: 20px;
  color: white;
}
</style>