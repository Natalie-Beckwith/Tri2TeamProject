# FRQ3 - Calculator


<form id="form">
  <label for="input">Input:</label><br>
  <input type="text" id="input" name="input"><br>
  <button type="submit" id="submit-button">Submit</button>
</form> 

<br/>

## Results
<!--- Table of results -->
<h2 id="result"></h2>

<!--- Access API -->
<script>
  document.getElementById('form').addEventListener('submit', (event) => {
    event.preventDefault();
    let input = document.getElementById('input').value;

    // POST
    const url = 'https://blognorte.tk/api/calculator/create?exp='+input;

    fetch(url, {method: 'POST', mode: 'no-cors'})                    
    .then((response) => {
      console.log("test");
      return response.then((data) => {
      document.getElementById("result").value = data.result;
      console.log(data.result);
      })
    });
  });
</script>