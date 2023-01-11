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
  function viewProfile(){
    window.location.href = location + '/profile';
  }

</script>

<style>
  #buttons{
    text-align: center;
  }


  </style>


