## Activities!
<!-- HTML table fragment for page -->
<style>
  table, th, td {
    border: 2px solid black;
    border-radius: 10px;
  }
  table.center {
    margin-left: auto;
    margin-right: auto;
  }
  th, td {
    text-align: center;
  } 
</style
<html>
<table style="width:100%">
  <thead>
  <tr>
    <th>Event</th>
    <th>Date</th>
    <th>Time</th>
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
<br>
<br>
{% comment %} 
<h2>Create</h2>
<form id="form">
<input type="text" placeholder="Event" id="new_event">
<input type="text" placeholder="Date" id="new_date">
<input type="text" placeholder="Time" id="new_time">
<input type="text" placeholder="Contact" id="new_contact">
<input type="text" placeholder="Description" id="new_description">
<input type="text" placeholder="Location" id="new_location">
<button type="submit" onclick="create()">Create</button>
</form> {% endcomment %}

</html>
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
            const time = document.createElement("td");
            const contact = document.createElement("td");
            const description = document.createElement("td");
            const location = document.createElement("td");
            // data is specific to the API
            event.innerHTML = row.event; 
            date.innerHTML = row.date;
            time.innerHTML = row.time; 
            contact.innerHTML = row.contact; 
            description.innerHTML = row.description; 
            location.innerHTML = row.location; 
            // this build td's into tr
            tr.appendChild(event);
            tr.appendChild(date);
            tr.appendChild(time);
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

  {% comment %} function create() {
    let newevent = document.getElementById("new_event").value;
    let newdate = document.getElementById("new_date").value;
    let newtime = document.getElementById("new_time").value;
    let newcontact = document.getElementById("new_contact").value;
    let newdescription = document.getElementById("new_description").value;
    let newlocation = document.getElementById("new_location").value;
    data = {event: newevent, date: newdate, time: newtime, contact: newcontact, description: newdescription, location: newlocation}
    var requestOptions = {
        method: 'POST',
        mode: 'cors',
        cache: 'no-cache',
        credentials: 'include',
        headers: {
            'Content-Type': 'application/json'
        },
        body: JSON.stringify(data)
    };
    fetch(
        `http://localhost:5962/api/activities/post/`,requestOptions
        )
        .then(response => response.text())
.then(result => {
        console.log(result);
        if (result == `Event is created successfully`) {
        alert("Event is created successfully");
        } else {
        alert("Error occurred during submission, reload and try again.");
        }
    })
    .catch(error => console.log('error', error));
    }

    // Example POST method implementation:
    async function create(url = 'http://localhost:5962/api/activities/post', data = {event: newevent, date: newdate, time: newtime, contact: newcontact, description: newdescription, location: newlocation}) {
      // Default options are marked with *
      const response = await fetch(url, {
        method: 'POST', // *GET, POST, PUT, DELETE, etc.
        mode: 'cors', // no-cors, *cors, same-origin
        cache: 'no-cache', // *default, no-cache, reload, force-cache, only-if-cached
        credentials: 'include', // include, *same-origin, omit
        headers: {
          'Content-Type': 'application/json'
        },
        body: JSON.stringify(data) // body data type must match "Content-Type" header
      });
      return response.json(); // parses JSON response into native JavaScript objects
    }
    
    postData('https://example.com/answer', { answer: 42 })
      .then((data) => {
        console.log(data); // JSON data parsed by `data.json()` call
      }); {% endcomment %}
    

</script>
