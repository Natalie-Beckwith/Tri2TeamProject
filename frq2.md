# Hello!
<div id="buttons">
<button onclick="viewProfile()">View your profile</button>
<button onclick="makeProfle()">Make a profile</button>
<button onclick="editProfile()">Edit your profile</button>
</div>
<script>
        function redirectToErrorPage() {
      window.location.href = location.origin + '/error';
    }
  async function viewProfile(){
    let response = await fetch('https://blognorte.tk/api/people/', { method: 'GET', headers: {"Accept":"application/json"} });
    let data = await response.json();
    if (data.status == "success"){
      console.log(data);
    }
    else{
      redirectToErrorPage();
    }
  }
</script>

<style>
  #buttons{
    text-align: center;
  }


  </style>


