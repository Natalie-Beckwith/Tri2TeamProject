# Hello!

<button onclick = "redirectToErrorPage()">View the current LightBoard</button>

<button onclick = "redirectToErrorPage()">Make a LightBoard</button>

<button onclick = "redirectToErrorPage()">View a specific row/column</button>


<script>

    function redirectToErrorPage() {
        window.location.href = location.origin + '/error';
  }

</script>
