## Storing Info About a Person FRQ

<table>

  <tr id="nameRow">
  </tr>

  <tr id="ageRow">
  </tr>

  <tr id="emailRow">
  </tr>

</table>

<script>
  
  function person() {
    
    result = document.getElementById("personInformation");
    fetch('https://serafina.tk/api/person/')
    .then(response => response.json())
    .then(data => {
      peopleData = data;
          // get row elements
            let nameRow = document.getElementById("nameRow");
            let ageRow = document.getElementById("ageRow");
            let emailRow = document.getElementById("emailRow");
            
            // clear table contents
            for (let j = 0; j < peopleData.length; j++){    

                nameRow.innerHTML = " ";
                ageRow.innerHTML = " ";
                emailRow.innerHTML = " ";

            }

            // add table contents
            for (let i = 0; i < peopleData.length; i++){  

                let header = document.createElement("th");
                header.setAttribute("id", i);
                header.innerHTML = peopleData[i].name;
                nameRow.appendChild(header);

                let newAgeRow = document.createElement("td");
                newAgeRow.setAttribute("id", i);
                newAgeRow.innerHTML = peopleData[i].age + " Years Old";
                ageRow.appendChild(newAgeRow);


                let newEmailRow = document.createElement("td");
                newEmailRow.setAttribute("id", i);
                newEmailRow.innerHTML = peopleData[i].email;
                emailRow.appendChild(newEmailRow);  
            }

        console.log(data);
        
  
      
      })
      
}
</script>

<style> 
button {
	width: 120px;
	height: 40px;
	font-size: 15px;
	background-color: #43B4E5;
	color: #fff;
	border: none;
	cursor: pointer;
}

p {
  font-size: 20px;
  color: white;
}
</style>

<button onclick="person()">Information About People</button>
<!-- <p id="personInformation"></p> -->