# Please fill out the information below to create your profile. 

<form id="profileForm" onSubmit="submitForm()">
  <label for="email">Email:</label>
  <input type="email" id="email" name="email" required>
  <label for="password">Password:</label>
  <input type="password" id="password" name="password" required>
  <br>
  <br>
  <label for="name">Name:</label>
  <input type="text" id="name" name="name" required>
  <br>
  <label for="dob">Date of birth:</label>
  <input type="date" id="dob" name="dobString" required>
  <br>
  <br>
  <label for="height">Height: (in cm)</label>
  <input type="number" id="height" name="height" min="0" required>
  <br>
  <label for="weight">Weight: (in lbs)</label>
  <input type="number" id="weight" name="weight" min="0" required>
  <br>
  <label for="freetime">Free Time: (minutes/week)</label>
  <input type="number" id="freetime" name="freetime" min="0" required>
  <br>
  <input type="submit" value="Submit">
</form>


<script>
async function submitForm(){
    event.preventDefault();
    const email = document.getElementById("email").value;
    const password = document.getElementById("password").value;
    const name = document.getElementById("name").value;
    const dob = document.getElementById("dob").value;
    const height = document.getElementById("height").value;
    const weight = document.getElementById("weight").value;
    const freetime = document.getElementById("freetime").value;
    let parts = dob.split("-");
    let newDateString = `${parts[1]}-${parts[2]}-${parts[0]}`;

    const data = {
        email: email,
        password: password,
        name: name,
        dob: newDateString,
        height: height,
        weight: weight,
        freetime: freetime
    };
    const params = new URLSearchParams();

    for (const [key, value] of Object.entries(data)) {
        params.append(key, value);
    }
    await checkEmail(email, params);
}

    async function createProfile(params){
        fetch("https://blognorte.tk/api/person/post", {
            method: "POST",
            headers: {
                "Content-Type": "application/x-www-form-urlencoded"
            },
            body: params
            })
            .then(response => response.text())
            .then(data => {
            console.log(data);
            if(data.includes("successfully")){
                alert("Profile created successfully!");
                window.location.href = location.origin + `/Tri2TeamProject/FRQs/frq2/profile?email=${params.get('email')}&password=${params.get('password')}`;
            }
            else{
                alert("Profile creation failed. Please try again.")
            }
            })
            .catch(error => {
            return console.error(error);
            });
    }


    async function checkEmail(email, params){
        const url = `https://blognorte.tk/api/person/`;
        const response = await fetch(url, {method: 'GET', headers:{"Accept":"application/json"}})
        const data = await response.json();
        const person = data.find(person => person.email === email);
        if(person){
            return alert("Email is already registered. Please try again.")
        }
        else{
            createProfile(params)
        }
    }

</script>

<style>
#profileForm {
    text-align: center;
}
</style>