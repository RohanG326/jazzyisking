<h2>Create</h2>
<form action="javascript:create()">
<input type="text" placeholder="Event" id="new_event">
<input type="text" placeholder="Date" id="new_date">
<input type="text" placeholder="Time" id="new_time">
<input type="text" placeholder="Contact" id="new_contact">
<input type="text" placeholder="Description" id="new_description">
<input type="text" placeholder="Location" id="new_location">
<button>Create</button>
</form>

<script>
    var url = "http://localhost:5962"
    // Authenticate endpoint

    function create(){
        // Set body to include login data
        let event = document.getElementById("new_event").value
        let date = document.getElementById("new_date").value
        let time = document.getElementById("new_time").value
        let contact = document.getElementById("new_contact").value
        let description = document.getElementById("new_description").value
        let location = document.getElementById("new_location").value
        let activitiespost_url = url + '/api/activities/post/?event=' + event + '&date='+ date + '&time='+ time +'&contact='+ contact + '&description='+ description + '&location=' + location;

        // Set Headers to support cross origin
        const requestOptions = {
            method: 'POST',
            mode: 'cors',
            cache: 'no-cache',
            credentials: 'include',
            headers: {
                "content-type": "application/json",
            },
        };

        // Fetch JWT
        fetch(activitiespost_url, requestOptions)
        .then(response => {
            // trap error response from Web API
            if (!response.ok) {
                const errorMsg = 'Post error: ' + response.status;
                alert(errorMsg);
                return;
            }
            // Success!!!
            // Redirect to Database location
          window.location.href = "/templates/fetchactivities";
        })
    }
</script>
