## Activities!
<!-- HTML table fragment for page -->

  <head>
    <link href="https://fonts.googleapis.com/css?family=Exo&display=swap" rel="stylesheet" />
  </head>
  <div class="img">
    <br>
    <br>
    <br>
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
<button class="addevent" onclick="window.location.href='/templates/createactivities';">Add Activity</button>

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

<script>
  // prepare HTML result container for new output
  const resultContainer = document.getElementById("result");

  // prepare URL
  var url = "https://samayacsa.tk/api/activities/";
  // Uncomment next line for localhost testing
  {% comment %} var url = "http://localhost:5962/api/activities/"; {% endcomment %}

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
          {% comment %} const errorMsg = 'Database response error: ' + response.status; {% endcomment %}
          const errorMsg = 'Please login to access the activities';

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
    {% comment %} The next line gives the response error {% endcomment %}
    {% comment %} td.innerHTML = err + ": " + url; {% endcomment %}
    {% comment %} This line is telling the user they are not signed in {% endcomment %}
    td.innerHTML = "Please login to access the activities";
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
    
    <style>
      table, th, td {
        border: 4px solid black;
        border-radius: 10px;
        background-color: rgba(72, 153, 228, .6);
        font-size: 30px;
        font-family: Exo;
        font-weight: Regular;
        color: rgba(0,0,0,1);
        border-radius: 40px;
        color: white
      }
      table.center {
        margin-left: auto;
        margin-right: auto;
      }
      th, td {
        text-align: center;
      } 
      th {
        font-size: 45px;

      }
      .img {
        width: 100%;
        height: 100%;
        background: url("../images/prettierlake.jpg");
        background-repeat: no-repeat;
        background-position: center center;
        background-size: cover;
        opacity: 1;
        position: absolute;
        top: 140px;
        left: 0px;
        overflow: hidden;
      }
    body {
      font-size: 26px;
      color: rgb(200, 200, 200);
    }
    
    .addevent {
      position: absolute;
      display: inline-block;
      background-color: rgb(72, 153, 228);
      padding: 5px;
      width: 330px;
      color: #ffffff;
      text-align: center;
      border: 4px #cccccc; 
      border-radius: 10px; 
      font-size: 28px; 
      cursor: pointer; 
      margin: 5px; 
      top: 20px;
      left: 1487px;
    }
    
    .event1 {
      width: 653px;
      color: rgba(0,0,0,1);
      position: absolute;
      top: 140px;
      left: 42px;
      font-size: 36px;
      font-family: Exo;
      font-weight: Regular;
      opacity: 1;
      text-align: left;
    }
    .event2 {
      width: 653px;
      color: rgba(0,0,0,1);
      position: absolute;
      top: 140px;
      left: 750px;
      font-size: 36px;
      font-family: Exo;
      font-weight: Regular;
      opacity: 1;
      text-align: left;
    }
    .event3 {
      width: 653px;
      color: rgba(0,0,0,1);
      position: absolute;
      top: 440px;
      left: 42px;
      font-size: 36px;
      font-family: Exo;
      font-weight: Regular;
      opacity: 1;
      text-align: left;
    }
    .event4 {
      width: 653px;
      color: rgba(0,0,0,1);
      position: absolute;
      top: 440px;
      left: 750px;
      font-size: 36px;
      font-family: Exo;
      font-weight: Regular;
      opacity: 1;
      text-align: left;
    }
    .event5 {
      width: 653px;
      color: rgba(0,0,0,1);
      position: absolute;
      top: 740px;
      left: 42px;
      font-size: 36px;
      font-family: Exo;
      font-weight: Regular;
      opacity: 1;
      text-align: left;
    }
    .event6 {
      width: 653px;
      color: rgba(0,0,0,1);
      position: absolute;
      top: 740px;
      left: 750px;
      font-size: 36px;
      font-family: Exo;
      font-weight: Regular;
      opacity: 1;
      text-align: left;
    }
    .v104_172 {
      width: 100%;
      height: 1024px;
      background: rgba(255,255,255,1);
      opacity: 1;
      position: relative;
      top: 0px;
      left: 0px;
      overflow: hidden;
    }
    .v104_193 {
      width: 100%;
      height: 100%;
      background: url("../images/v104_193.png");
      background-repeat: no-repeat;
      background-position: center center;
      background-size: cover;
      opacity: 1;
      position: relative;
      top: 0px;
      left: 0px;
      overflow: hidden;
    }
    .v104_174 {
      width: 99px;
      color: rgba(255,255,255,1);
      position: absolute;
      top: 23px;
      left: 47px;
      font-family: Exo;
      font-weight: Regular;
      font-size: 36px;
      opacity: 1;
      text-align: left;
    }
    .v105_36 {
      width: 99px;
      color: rgba(255,255,255,1);
      position: absolute;
      top: 23px;
      left: 47px;
      font-family: Exo;
      font-weight: Regular;
      font-size: 36px;
      opacity: 1;
      text-align: left;
    }
    .v104_175 {
      width: 143px;
      color: rgba(255,255,255,1);
      position: absolute;
      top: 23px;
      left: 197px;
      font-family: Exo;
      font-weight: Regular;
      font-size: 36px;
      opacity: 1;
      text-align: left;
    }
    .v104_176 {
      width: 139px;
      color: rgba(255,255,255,1);
      position: absolute;
      top: 23px;
      left: 377px;
      font-family: Exo;
      font-weight: Regular;
      font-size: 36px;
      opacity: 1;
      text-align: left;
    }
    .v104_177 {
      width: 150px;
      color: rgba(255,255,255,1);
      position: absolute;
      top: 23px;
      left: 549px;
      font-family: Exo;
      font-weight: Regular;
      font-size: 36px;
      opacity: 1;
      text-align: left;
    }
    .v104_178 {
      width: 168px;
      color: rgba(255,255,255,1);
      position: absolute;
      top: 23px;
      left: 1260px;
      font-family: Exo;
      font-weight: Regular;
      font-size: 36px;
      opacity: 1;
      text-align: left;
    }
    .v104_194 {
      width: 710px;
      height: 290px;
      background: rgba(217,217,217,1);
      opacity: 1;
      position: absolute;
      top: 130px;
      left: 12px;
      border-top-left-radius: 20px;
      border-top-right-radius: 20px;
      border-bottom-left-radius: 20px;
      border-bottom-right-radius: 20px;
      overflow: hidden;
    }
    .v104_195 {
      width: 203px;
      color: rgba(0,0,0,1);
      position: absolute;
      top: 220px;
      left: 42px;
      font-family: Exo;
      font-weight: Regular;
      opacity: 1;
      text-align: left;
    }
    .v104_196 {
      width: 360px;
      height: 60px;
      background: rgba(60,130,194,1);
      opacity: 1;
      position: absolute;
      top: 334px;
      left: 171px;
      border-top-left-radius: 20px;
      border-top-right-radius: 20px;
      border-bottom-left-radius: 20px;
      border-bottom-right-radius: 20px;
      overflow: hidden;
    }
    .v104_197 {
      width: 209px;
      color: rgba(255,255,255,1);
      position: absolute;
      top: 340px;
      left: 253px;
      font-family: Exo;
      font-weight: Regular;
      font-size: 36px;
      opacity: 1;
      text-align: left;
    }
    .v104_198 {
      width: 710px;
      height: 290px;
      background: rgba(217,217,217,1);
      opacity: 1;
      position: absolute;
      top: 430px;
      left: 14px;
      border-top-left-radius: 20px;
      border-top-right-radius: 20px;
      border-bottom-left-radius: 20px;
      border-bottom-right-radius: 20px;
      overflow: hidden;
    }
    .v104_199 {
      width: 200px;
      color: rgba(0,0,0,1);
      position: absolute;
      top: 500px;
      left: 44px;
      font-family: Exo;
      font-weight: Regular;
      opacity: 1;
      text-align: left;
    }
    .v104_200 {
      width: 360px;
      height: 60px;
      background: rgba(60,130,194,1);
      opacity: 1;
      position: absolute;
      top: 634px;
      left: 173px;
      border-top-left-radius: 20px;
      border-top-right-radius: 20px;
      border-bottom-left-radius: 20px;
      border-bottom-right-radius: 20px;
      overflow: hidden;
    }
    .v104_201 {
      width: 209px;
      color: rgba(255,255,255,1);
      position: absolute;
      top: 640px;
      left: 255px;
      font-family: Exo;
      font-weight: Regular;
      font-size: 36px;
      opacity: 1;
      text-align: left;
    }
    .v104_202 {
      width: 710px;
      height: 290px;
      background: rgba(217,217,217,1);
      opacity: 1;
      position: absolute;
      top: 130px;
      left: 730px;
      border-top-left-radius: 20px;
      border-top-right-radius: 20px;
      border-bottom-left-radius: 20px;
      border-bottom-right-radius: 20px;
      overflow: hidden;
    }
    .v104_203 {
      width: 200px;
      color: rgba(0,0,0,1);
      position: absolute;
      top: 200px;
      left: 760px;
      font-family: Exo;
      font-weight: Regular;
      opacity: 1;
      text-align: left;
    }
    .v104_204 {
      width: 360px;
      height: 60px;
      background: rgba(60,130,194,1);
      opacity: 1;
      position: absolute;
      top: 334px;
      left: 889px;
      border-top-left-radius: 20px;
      border-top-right-radius: 20px;
      border-bottom-left-radius: 20px;
      border-bottom-right-radius: 20px;
      overflow: hidden;
    }
    .v104_205 {
      width: 209px;
      color: rgba(255,255,255,1);
      position: absolute;
      top: 340px;
      left: 971px;
      font-family: Exo;
      font-weight: Regular;
      font-size: 36px;
      opacity: 1;
      text-align: left;
    }
    .v104_206 {
      width: 710px;
      height: 290px;
      background: rgba(217,217,217,1);
      opacity: 1;
      position: absolute;
      top: 430px;
      left: 730px;
      border-top-left-radius: 20px;
      border-top-right-radius: 20px;
      border-bottom-left-radius: 20px;
      border-bottom-right-radius: 20px;
      overflow: hidden;
    }
    .v104_207 {
      width: 346px;
      color: rgba(0,0,0,1);
      position: absolute;
      top: 540px;
      left: 760px;
      font-family: Exo;
      font-weight: Regular;
      opacity: 1;
      text-align: left;
    }
    .v104_208 {
      width: 360px;
      height: 60px;
      background: rgba(60,130,194,1);
      opacity: 1;
      position: absolute;
      top: 634px;
      left: 889px;
      border-top-left-radius: 20px;
      border-top-right-radius: 20px;
      border-bottom-left-radius: 20px;
      border-bottom-right-radius: 20px;
      overflow: hidden;
    }
    .v104_209 {
      width: 209px;
      color: rgba(255,255,255,1);
      position: absolute;
      top: 640px;
      left: 971px;
      font-family: Exo;
      font-weight: Regular;
      font-size: 36px;
      opacity: 1;
      text-align: left;
    }
    .v104_210 {
      width: 710px;
      height: 290px;
      background: rgba(217,217,217,1);
      opacity: 1;
      position: absolute;
      top: 730px;
      left: 14px;
      border-top-left-radius: 20px;
      border-top-right-radius: 20px;
      border-bottom-left-radius: 20px;
      border-bottom-right-radius: 20px;
      overflow: hidden;
    }
    .v104_211 {
      width: 347px;
      color: rgba(0,0,0,1);
      position: absolute;
      top: 800px;
      left: 44px;
      font-family: Exo;
      font-weight: Regular;
      opacity: 1;
      text-align: left;
    }
    .v104_212 {
      width: 360px;
      height: 60px;
      background: rgba(60,130,194,1);
      opacity: 1;
      position: absolute;
      top: 934px;
      left: 173px;
      border-top-left-radius: 20px;
      border-top-right-radius: 20px;
      border-bottom-left-radius: 20px;
      border-bottom-right-radius: 20px;
      overflow: hidden;
    }
    .v104_213 {
      width: 209px;
      color: rgba(255,255,255,1);
      position: absolute;
      top: 940px;
      left: 255px;
      font-family: Exo;
      font-weight: Regular;
      font-size: 36px;
      opacity: 1;
      text-align: left;
    }
    .v104_214 {
      width: 710px;
      height: 290px;
      background: rgba(217,217,217,1);
      opacity: 1;
      position: absolute;
      top: 730px;
      left: 730px;
      border-top-left-radius: 20px;
      border-top-right-radius: 20px;
      border-bottom-left-radius: 20px;
      border-bottom-right-radius: 20px;
      overflow: hidden;
    }
    .v104_215 {
      width: 346px;
      color: rgba(0,0,0,1);
      position: absolute;
      top: 800px;
      left: 760px;
      font-family: Exo;
      font-weight: Regular;
      opacity: 1;
      text-align: left;
    }
    .v104_216 {
      width: 360px;
      height: 60px;
      background: rgba(60,130,194,1);
      opacity: 1;
      position: absolute;
      top: 934px;
      left: 889px;
      border-top-left-radius: 20px;
      border-top-right-radius: 20px;
      border-bottom-left-radius: 20px;
      border-bottom-right-radius: 20px;
      overflow: hidden;
    }
    .v104_217 {
      width: 209px;
      color: rgba(255,255,255,1);
      position: absolute;
      top: 940px;
      left: 971px;
      font-family: Exo;
      font-weight: Regular;
      font-size: 36px;
      opacity: 1;
      text-align: left;
    }
    .v105_6 {
      width: 111px;
      color: rgba(255,255,255,1);
      position: absolute;
      top: 23px;
      left: 732px;
      font-family: Exo;
      font-weight: Regular;
      font-size: 36px;
      opacity: 1;
      text-align: left;
    }
  </style>