### Enter your information below to access your profile.
<form id='login'>
  <label for="email">Email:</label>
  <input type="email" id="email" name="email" placeholder="example@gmail.com" required>

  <label for="password">Password:</label>
  <input type="password" id="password" name="password" placeholder="Enter your password" required>

  <input type="submit" id="submit" value="Submit">

</form>

<div id="profile-info">
  <h1 id='name'></h1>
  <h1 id='id'></h1>
  <h1 id='email'></h1>
  <h1 id='age'></h1>
  <h1 id='height'></h1>
  <h1 id='weight'></h1>
  <h1 id="freetime"></h1>
  <button onclick="editProfile()">Edit your profile</button>
</div>
<div id="profile-stats">
  <h1 id='stats'>Stats</h1>
  <li id="stats-list"></li>
</div>

<style>

body{
  text-align: center;
}

#profile-info{
  display: none;
}

#profile-stats{
  display: none;
}
</style>


<script>
  const emailInput = document.getElementById("email");
  const passwordInput = document.getElementById("password");
  const form = document.getElementById('login');
  const profile = document.getElementById('profile-info');
  const profileStats = document.getElementById('profile-stats');
  form.addEventListener('submit', async event =>{
    event.preventDefault();
    const email = event.target.elements.email.value
    const password = event.target.elements.password.value
    await verifyEmail(email, password);

  })

  function editProfileBut(){
    
  }


async function showProfile(data, profile){
  let name = document.getElementById('name');
  let id = document.getElementById('id');
  let email = document.getElementById('email');
  let password = document.getElementById('password');
  let age = document.getElementById('age');
  let height = document.getElementById('height');
  let weight = document.getElementById('weight');
  let freetime = document.getElementById('freetime');

  name.innerHTML = data.name;
  id.innerHTML = `ID: ${data.id}`;
  email.innerHTML = data.email;  
  age.innerHTML = `${data.age} years old`;
  height.innerHTML = `Height: ${cmToFeetInches(data.height)}`;
  weight.innerHTML = `Weight: ${data.weight} lbs`;
  freetime.innerHTML = `Freetime: ${minutesToHourMinutes(data.freetime)} per week`;
  profile.style.display = "block";
}

async function showStats(stats, profileStats){
  let statslist = document.getElementById('stats-list');

  Object.keys(stats).forEach(async key => {
    statslist.innerHTML += `<li>${key}: ${stats[key]["steps"]}</li>`;
  })
  profileStats.style.display = "block";
}

function cmToFeetInches(cm) {
  var inches = cm / 2.54;
  var feet = Math.floor(inches / 12);
  inches = Math.round(inches % 12);
  return feet + "ft " + inches + "in";
}

function minutesToHourMinutes(min){
  let hours = Math.floor(min / 60);
  let minutes = min % 60;
  return hours + " hours " + minutes + " minutes";
}

async function verifyEmail(email, password){
    const url = `https://blognorte.tk/api/person/`;
    const response = await fetch(url, {method: 'GET', headers:{"Accept":"application/json"}})
    const data = await response.json();
    const person = data.find(person => person.email === email);
    
    if(person){
      if(person.password === password){
        showProfile(person, profile);
        if(Object.keys(person.stats).length > 0){
          showStats(person.stats, profileStats)
        }
      }
      else{
        alert("Incorrect password");
      }
    }
    else{
      alert("Email not found");
    }

  }

</script>