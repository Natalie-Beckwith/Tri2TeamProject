# Hello!

<button onclick="redirectToErrorPage()">View your profile</button>
<button onclick="redirectToErrorPage()">Make a profile</button>
<button onclick="redirectToErrorPage()">Edit your profile</button>

<script>
    
        function redirectToErrorPage() {
    window.location.href = location.origin + '/error';
  }

</script>


