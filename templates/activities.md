<html>
  {% comment %} <script>
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
  </script> {% endcomment %}
  <head>
    <link href="https://fonts.googleapis.com/css?family=Exo&display=swap" rel="stylesheet" />
  </head>
    <body>
        <div class="v104_172">
        <div class="v104_193"></div>
        {% comment %} <button onclick="window.location.href='/jazzyisking/templates/createactivities';">Add Activity</button> {% endcomment %}
        <button onclick="window.location.href='/templates/createactivities';">Add Activity</button>
        <div class="v104_194"></div>
        <div class="v104_202"></div>
        <div class="v104_198"></div>
        <div class="v104_206"></div>
        <div class="v104_210"></div>
        <div class="v104_214"></div>
        <span class="event1">Meeting</span>
        <span class="event2">Hike</span>
        <span class="event3">Bonfire</span>
        <span class="event4">Dinner</span>
        <span class="event5">Lunch</span>
        <span class="event6">Party</span>
        <span class="v104_195">Date: January 3, 2023
        Location: 16601 Nighthawk Ln, San Diego, CA 92127
        Number of Participants: 34</span>
        <div class="v104_196"></div>
<span class="v104_197">Count me in!</span>
<span class="v104_199">Date: January 11, 2023
Location: La Jolla Beach
Number of Participants: 28</span>
<div class="v104_200"></div>
<span class="v104_201">Count me in!</span>
<span class="v104_203">Date: January 6, 2023
Location: Torrey Pines
Number of Participants: 14</span>
<div class="v104_204"></div>
<span class="v104_205">Count me in!</span>
<span class="v104_207">Date: January 16, 2023
Location: McDonalds
Number of Participants: 23</span>
<div class="v104_208">
</div><span class="v104_209">Count me in!</span>
<span class="v104_211">Date: January 27, 2023
Location: Taco Bell
Number of Participants: 29</span><div class="v104_212"></div><span class="v104_213">Count me in!</span>
<span class="v104_215">Date: January 31, 2023
Location: Mr. Mort’s House
Number of Participants: 67</span><div class="v104_216"></div><span class="v104_217">Count me in!</span>
    </div>
  </body>
</html> 
<br/><br/> 

<style>* {
  box-sizing: border-box;
}
body {
  font-size: 14px;
}

button {
  position: absolute;
  display: inline-block;
  background-color: #3c82c2;
  padding: 5px;
  width: 330px;
  color: #ffffff;
  text-align: center;
  border: 4px #cccccc; 
  border-radius: 10px; 
  font-size: 28px; 
  cursor: pointer; 
  margin: 5px; 
  top: 35px;
  left: 27px;
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