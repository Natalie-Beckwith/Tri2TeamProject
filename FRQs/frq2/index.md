# Hello!
<div id="buttons">
<button onclick="viewProfile()">View your profile</button>
<button onclick="makeProfile()">Make a profile</button>
<button onclick="editProfile()">Edit your profile</button>
</div>
<script>
    function redirectToErrorPage() {
      window.location.href = location.origin + '/error';
    }
  function viewProfile(){
    window.location.href = location + '/profile';
  }
  function makeProfile(){
    window.location.href = location + 'makeProfile';
  }

</script>

<style>
  #buttons{
    text-align: center;
  }


  </style>


