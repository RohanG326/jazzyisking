## SQL Database
<!-- HTML table fragment for page -->
<html>
  <table class="races" border="1" align='left' cellspacing=2 cellpadding=5 id="data_table" border=1>
  <thead>
  <tr>
    <th>Name</th>
    <th>ID</th>
    <th>Age</th>
  </tr>
  </thead>
  <tbody id="result">
    <!-- javascript generated data -->
  </tbody>
    <!-- <head>
      <meta charset="utf-8" />
      <title>F1 Races</title>
      <meta name="description" content="F1 Races and their Information." /> -->
    
  </table>
  <tr>
  <td><input type="text" id="new_name"></td>
  <td><input type="text" id="new_country"></td>
  <td><input type="text" id="new_age"></td>
  <td><input type="button" class="add" onclick="add_row();" value="Add Row"></td>
  <td>

  <input type="button" id="edit_button1" value="Edit" class="edit" onclick="edit_row('1')">
  <input type="button" id="save_button1" value="Save" class="save" onclick="save_row('1')">
  <input type="button" value="Delete" class="delete" onclick="delete_row('1')">
  
  <style>
    table.center {
      margin-left: auto;
      margin-right: auto;
    }
      *{
      font-family: "Inter", sans-serif;
    }
    body{
      font-size: 1rem;
      font-weight: 400;aa
      line-height: 1.5;
      text-align: left;
    }
    .card{
      border-style: round;
      border-radius: 5px;
      border-width: 20px;
      padding-top: 1.25rem;
      padding-right: 1.25rem;
      padding-bottom: 1.25rem;
      padding-left: 1.25rem;
      background-color: #fcf8f7; 
      width:80%;
      margin-left: 8%;
      margin-top: 2%;
      margin-bottom: 2%;
      position: relative;
      column;flex-direction:column;min-width:0;
      display:-ms-flexbox;display:flex;
      }
    .card-title{
      margin-left:5px; 
      margin-top:5px;
    }
    .form-control{
      margin-left:5px; 
      border-style: round;
      border-radius: 5px;
      border-width: 2px; 
      width: 98%;
      length: 100%;
      font-family: sans-serif;
      padding: 0.375rem 0.75rem;
      font-size: 1rem;
      font-weight: 400;
      line-height: 1.5;
      color: #495057;
      background-color: #fff;
      background-clip: padding-box;
      border: 1px solid #ced4da;
    }
    .form-group {
      margin-bottom: 1rem;
    }
  </style>
</html>



<!-- Script is layed out in a sequence (no function) and will execute when page is loaded -->
<script>
  // prepare HTML result container for new output
  const resultContainer = document.getElementById("result");

  // prepare URL
  //var url = "https://spring.nighthawkcodingsociety.com/api/person/";
  // Uncomment next line for localhost testing
  var url = "http://localhost:5962/api/person/";

  // set options for cross origin header request
  const options = {
    method: 'GET', // *GET, POST, PUT, DELETE, etc.
    mode: 'cors', // no-cors, *cors, same-origin
    cache: 'default', // *default, no-cache, reload, force-cache, only-if-cached
    credentials: 'include', // include, *same-origin, omit
    headers: {
      'Content-Type': 'application/json',
    },
  };

  // fetch the API
  fetch(url, options)
    // response is a RESTful "promise" on any successful fetch
    .then(response => {
      // check for response errors and display
      if (response.status !== 200) {
          const errorMsg = 'Database response error: ' + response.status;
          console.log(errorMsg);
          const tr = document.createElement("tr");
          const td = document.createElement("td");
          td.innerHTML = errorMsg;
          tr.appendChild(td);
          resultContainer.appendChild(tr);
          return;
      }
      // valid response will contain json data
      response.json().then(data => {
          console.log(data);
          for (const row of data) {
            // tr and td build out for each row
            const tr = document.createElement("tr");
            const name = document.createElement("td");
            const id = document.createElement("td");
            const age = document.createElement("td");
            // data is specific to the API
            name.innerHTML = row.name; 
            id.innerHTML = row.email; 
            age.innerHTML = row.age; 
            // this build td's into tr
            tr.appendChild(name);
            tr.appendChild(id);
            tr.appendChild(age);
            // add HTML to container
            resultContainer.appendChild(tr);
          }
      })
  })
  // catch fetch errors (ie ACCESS to server blocked)
  .catch(err => {
    console.error(err);
    const tr = document.createElement("tr");
    const td = document.createElement("td");
    td.innerHTML = err + ": " + url;
    tr.appendChild(td);
    resultContainer.appendChild(tr);
  });
</script>