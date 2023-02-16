## SQL Database
<!-- HTML table fragment for page -->
<html>
<table>
  <thead>
  <tr>
    <th>Event</th>
    <th>Date</th>
    <th>Contact</th>
    <th>Description</th>
    <th>Location</th>
  </tr>
  </thead>
  <tbody id="result">
    <!-- javascript generated data -->
  </tbody>
</table>
<!-- Script is layed out in a sequence (no function) and will execute when page is loaded -->
<script>
  // prepare HTML result container for new output
  const resultContainer = document.getElementById("result");

  // prepare URL
  //var url = "https://spring.nighthawkcodingsociety.com/api/person/";
  // Uncomment next line for localhost testing
  var url = "http://localhost:5962/api/activities/";

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
            const event = document.createElement("td");
            const date = document.createElement("td");
            const contact = document.createElement("td");
            const description = document.createElement("td");
            const location = document.createElement("td");
            // data is specific to the API
            event.innerHTML = row.event; 
            date.innerHTML = row.date; 
            contact.innerHTML = row.contact; 
            description.innerHTML = row.description; 
            location.innerHTML = row.location; 
            // this build td's into tr
            tr.appendChild(event);
            tr.appendChild(date);
            tr.appendChild(contact);
            tr.appendChild(description);
            tr.appendChild(location);

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
</html>