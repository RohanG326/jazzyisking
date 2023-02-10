<html>
    <head>
        <link href="https://fonts.googleapis.com/css?family=Exo&display=swap" rel="stylesheet" />
    </head>
    <body><!-- <table>
    <tr>
        <td><a href="/jazzyisking">Home</a></td>
        <td><a href="/jazzyisking/templates/designplan">Design Plan</a></td>
        <td><a href="/jazzyisking/templates/login">Log In</a></td>
        <td><a href="/jazzyisking/templates/signup">Sign Up</a></td>
        <td><a href="/jazzyisking/templates/calendar">Calendar</a></td>
        <td><a href="/jazzyisking/templates/home">Home</a></td>
    </tr>
        </table> -->
        <!-- <div class="v87_2">
        <div class="v104_15"></div>
        <div class="v90_2"></div> -->
        <!-- <a class="v87_4" href="/jazzyisking/templates/home">Home</a>
        <a class="v87_5" href="/jazzyisking/templates/calendar">Calender</a>
        <span class="v87_7">Itinerary</span>
        <span class="v87_8">Activities</span>
        <a class="v87_9" href="/jazzyisking/templates/login">Login</a> -->
        <!-- </div><span class="v94_10">Type in Password</span>
        <span class="v94_5">Username</span>
        <span class="v94_6">Password</span>
        <span class="v90_3">Login</span>
        <div class="name"></div>
        <div class="name"></div>
        <span class="v94_9">Type in Username</span>
        <div class="v94_11">
        </div><span class="v94_12">Login</span>
        <a class="v94_13" href="/jazzyisking/templates/signup">New User? Click here to sign up</a>
        </div> -->
        <!-- <div class="p-5 mb-4 bg-light text-dark rounded-3">
                <form name="f" action="/authenticate/" method="POST">
                    <table>
                        <tbody><tr><th><label for="username">Email</label></th></tr>
                        <tr><td><input type="email" id="username" name="username" size="20" required=""></td></tr>
                        <tr><th><label for="password">Password</label></th></tr>
                        <tr><td><input type="password" id="password" name="password" size="20" required=""></td></tr>
                        <tr><th><input type="submit" value="Submit"></th></tr>
                        <tr><td><a href="/templates/signup">Sign Up</a></td></tr>
                    </tbody></table>
                </form>
            </div>
    </body> 
</html> -->
<form action="javascript:login_user()">
    <p><label>
        User ID:
        <input type="text" name="uid" id="uid" required>
    </label></p>
    <p><label>
        Password:
        <input type="password" name="password" id="password" required>
    </label></p>
    <p>
        <button>Login</button>
    </p>
</form>

<script>
    // URL for deployment
    //var url = "https://spring.nighthawkcodingsociety.com"
    // Comment out next line for local testing
   var url = "http://localhost:5962"
    // Authenticate endpoint
    const login_url = url + '/authenticate';


    function login_user(){
        // Set body to include login data
        const body = {
            email: document.getElementById("uid").value,
            password: document.getElementById("password").value,
        };

        // Set Headers to support cross origin
        const requestOptions = {
            method: 'POST',
            mode: 'cors', // no-cors, *cors, same-origin
            cache: 'no-cache', // *default, no-cache, reload, force-cache, only-if-cached
            credentials: 'include', // include, *same-origin, omit
            body: JSON.stringify(body),
            headers: {
                "content-type": "application/json",
            },
        };

        // Fetch JWT
        fetch(login_url, requestOptions)
        .then(response => {
            // trap error response from Web API
            if (!response.ok) {
                const errorMsg = 'Login error: ' + response.status;
                console.log(errorMsg);
                return;
            }
            // Success!!!
            // Redirect to Database location
          window.location.href = "/templates/home";
        })
    }


</script>
<!-- <style>* {
  box-sizing: border-box;
}
body {
  font-size: 14px;
}
.v87_2 {
  width: 100%;
  height: 1024px;
  background: rgba(255,255,255,1);
  opacity: 1;
  position: relative;
  top: 0px;
  left: 0px;
  overflow: hidden;
}
.v104_15 {
  width: 100%;
  height: 100%;
  background: url("../images/v104_15.png");
  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover;
  opacity: 1;
  position: absolute;
  top: 3px;
  left: 0px;
  overflow: hidden;
}
.v87_4 {
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
.v87_5 {
  width: 147px;
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
.v87_7 {
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
.v87_8 {
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
.v87_9 {
  width: 91px;
  color: rgba(255,255,255,1);
  position: absolute;
  top: 23px;
  left: 1328px;
  font-family: Exo;
  font-weight: Regular;
  font-size: 36px;
  opacity: 1;
  text-align: left;
}
.v90_2 {
  width: 456px;
  height: 570px;
  background: rgba(255,255,255,1);
  opacity: 1;
  position: absolute;
  top: 175px;
  left: 492px;
}
.v94_10 {
  width: 161px;
  color: rgba(120,120,120,1);
  position: absolute;
  top: 653px;
  left: 567px;
  font-family: Exo;
  font-weight: Regular;
  font-size: 20px;
  opacity: 1;
  text-align: left;
}
.v94_5 {
  width: 96px;
  color: rgba(0,0,0,1);
  position: absolute;
  top: 453px;
  left: 555px;
  font-family: Exo;
  font-weight: Regular;
  font-size: 20px;
  opacity: 1;
  text-align: left;
}
.v94_6 {
  width: 90px;
  color: rgba(0,0,0,1);
  position: absolute;
  top: 610px;
  left: 558px;
  font-family: Exo;
  font-weight: Regular;
  font-size: 20px;
  opacity: 1;
  text-align: left;
}
.v90_3 {
  width: 121px;
  color: rgba(0,0,0,1);
  position: absolute;
  top: 356px;
  left: 659px;
  font-family: Exo;
  font-weight: Regular;
  font-size: 48px;
  opacity: 1;
  text-align: left;
}
.name {
  color: #fff;
}
.name {
  color: #fff;
}
.v94_9 {
  width: 166px;
  color: rgba(120,120,120,1);
  position: absolute;
  top: 504px;
  left: 567px;
  font-family: Exo;
  font-weight: Regular;
  font-size: 20px;
  opacity: 1;
  text-align: left;
}
.v94_11 {
  width: 325px;
  height: 60px;
  background: rgba(23,64,110,1);
  opacity: 1;
  position: absolute;
  top: 720px;
  left: 555px;
  border-top-left-radius: 20px;
  border-top-right-radius: 20px;
  border-bottom-left-radius: 20px;
  border-bottom-right-radius: 20px;
  overflow: hidden;
}
.v94_12 {
  width: 76px;
  color: rgba(255,255,255,1);
  position: absolute;
  top: 730px;
  left: 670px;
  font-family: Exo;
  font-weight: Regular;
  font-size: 30px;
  opacity: 1;
  text-align: left;
}
.v94_13 {
  width: 334px;
  color: url("../images/v94_13.png");
  position: absolute;
  top: 817px;
  left: 551px;
  font-family: Exo;
  font-weight: Regular;
  font-size: 23px;
  opacity: 1;
  text-align: left;
}
.v105_3 {
  width: 111px;
  color: rgba(255,255,255,1);
  position: absolute;
  top: 23px;
  left: 740px;
  font-family: Exo;
  font-weight: Regular;
  font-size: 36px;
  opacity: 1;
  text-align: left;
}
</style> -->