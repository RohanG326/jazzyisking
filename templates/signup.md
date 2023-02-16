<html>
    <head>
        <link href="https://fonts.googleapis.com/css?family=Exo&display=swap" rel="stylesheet" />
    </head>
    <body>
        <div class="v94_14">
        <div class="v104_17"></div>
        <div class="v94_21"></div>
        </div>
    </body>
</html>

<script>
    // URL for deployment
    //var url = "https://spring.nighthawkcodingsociety.com"
    // Comment out next line for local testing
   var url = "http://localhost:5962"
    // Authenticate endpoint
    const sign_up_url = url + '/api/person/post';


    function sign_up_user(){
        // Set body to include login data
        const body = {
            email: document.getElementById("uid").value,
            password: document.getElementById("password").value,
            name: document.getElementById("name1").value,
            dob: document.getElementById("dob").value,
        };

        // Set Headers to support cross origin
        const requestOptions = {
            method: 'POST',

            // mode: 'cors', // no-cors, *cors, same-origin
            // cache: 'default', // *default, no-cache, reload, force-cache, only-if-cached
            // credentials: 'omit', // include, *same-origin, omit
            body: JSON.stringify(body),
            headers: {
                "content-type": "application/json",
            },
        };

        // Fetch JWT
        fetch(sign_up_url, requestOptions)
        .then(response => {
            // trap error response from Web API
            if (!response.ok) {
                const errorMsg = 'Login error: ' + response.status;
                console.log(errorMsg);
                return;
            }
            // Success!!!
            // Redirect to Database location
          window.location.href = "/templates/login";
        })
    }
</script>

<html>
<form action="javascript:sign_up_user()">
    <p><label>
        Email:
        <input type="text" name="uid" id="uid" required>
    </label></p>
    <p><label>
        Password:
        <input type="password" name="password" id="password" required>
    </label></p>
    <p><label>
        Name:
        <input type="text" name="name1" id="name1" required>
    </label></p>
    <p><label>
        Date Of Birth(mm-dd-yyyy):
        <input type="text" name="dob" id="dob" required>
    </label></p>
    <p>
        <button>Sign Up</button>
    </p>
</form>
<a class="v94_31" href="/jazzyisking/templates/login">Already have an account? Click here to login</a>
</html>


<!-- <style>* {
  box-sizing: border-box;
}
body {
  font-size: 14px;
}
.v94_14 {
    width: 100%;
    height: 1024px;
    background: rgba(255,255,255,1);
    opacity: 1;
    position: relative;
    top: 0px;
    right: 0px;
    overflow: hidden;
}
.v104_17 {
  width: 100%;
  height: 100%;
  background: url("../images/v104_17.png");
  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover;
  opacity: 1;
  position: relative;
  top: 0px;
  left: 0px;
  overflow: hidden;
}
.v94_21 {
  width: 456px;
  height: 730px;
  background: rgba(255,255,255,1);
  opacity: 1;
  position: absolute;
  top: 170px;
  left: 492px;
}
.v94_16 {
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
.v94_17 {
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
.v94_18 {
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
.v94_19 {
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
.v94_20 {
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
.v94_22 {
  width: 161px;
  color: rgba(120,120,120,1);
  position: absolute;
  top: 671px;
  left: 567px;
  font-family: Exo;
  font-weight: Regular;
  font-size: 20px;
  opacity: 1;
  text-align: left;
}
.v94_23 {
  width: 96px;
  color: rgba(0,0,0,1);
  position: absolute;
  top: 522px;
  left: 555px;
  font-family: Exo;
  font-weight: Regular;
  font-size: 20px;
  opacity: 1;
  text-align: left;
}
.v94_24 {
  width: 90px;
  color: rgba(0,0,0,1);
  position: absolute;
  top: 628px;
  left: 558px;
  font-family: Exo;
  font-weight: Regular;
  font-size: 20px;
  opacity: 1;
  text-align: left;
}
.v94_25 {
  width: 168px;
  color: rgba(0,0,0,1);
  position: absolute;
  top: 229px;
  left: 634px;
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
.v94_28 {
  width: 166px;
  color: rgba(120,120,120,1);
  position: absolute;
  top: 573px;
  left: 567px;
  font-family: Exo;
  font-weight: Regular;
  font-size: 20px;
  opacity: 1;
  text-align: left;
}
.v94_32 {
  width: 170px;
  color: rgba(120,120,120,1);
  position: absolute;
  top: 466px;
  left: 561px;
  font-family: Exo;
  font-weight: Regular;
  font-size: 20px;
  opacity: 1;
  text-align: left;
}
.v94_33 {
  width: 102px;
  color: rgba(0,0,0,1);
  position: absolute;
  top: 317px;
  left: 549px;
  font-family: Exo;
  font-weight: Regular;
  font-size: 20px;
  opacity: 1;
  text-align: left;
}
.v94_34 {
  width: 99px;
  color: rgba(0,0,0,1);
  position: absolute;
  top: 423px;
  left: 552px;
  font-family: Exo;
  font-weight: Regular;
  font-size: 20px;
  opacity: 1;
  text-align: left;
}
.name {
  color: #fff;
}
.name {
  color: #fff;
}
.v94_37 {
  width: 173px;
  color: rgba(120,120,120,1);
  position: absolute;
  top: 368px;
  left: 561px;
  font-family: Exo;
  font-weight: Regular;
  font-size: 20px;
  opacity: 1;
  text-align: left;
}
.v94_29 {
  width: 325px;
  height: 60px;
  background: rgba(23,64,110,1);
  opacity: 1;
  position: absolute;
  top: 739px;
  left: 555px;
  border-top-left-radius: 20px;
  border-top-right-radius: 20px;
  border-bottom-left-radius: 20px;
  border-bottom-right-radius: 20px;
  overflow: hidden;
}
.v94_30 {
  width: 105px;
  color: rgba(255,255,255,1);
  position: absolute;
  top: 747px;
  left: 670px;
  font-family: Exo;
  font-weight: Regular;
  font-size: 30px;
  opacity: 1;
  text-align: left;
}
.v94_31 {
  width: 380px;
  color: url("../images/v94_31.png");
  position: absolute;
  top: 819px;
  left: 530px;
  font-family: Exo;
  font-weight: Regular;
  font-size: 23px;
  opacity: 1;
  text-align: center;
}
.v105_4 {
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