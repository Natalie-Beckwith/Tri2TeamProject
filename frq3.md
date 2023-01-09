# FRQ3 - Calculator


<form id="form">
  <label for="input">Input:</label><br>
  <input type="text" id="input" name="input"><br>
  <button type="submit" id="submit-button">Submit</button>
</form> 

<br/>

## Results
<!--- Table of results -->
<table id="table">
  <tr>
    <th>Input</th>
    <th>Tokens</th> 
    <th>Postfix</th>
    <th>Calculation</th>
  </tr>
</table>

<!--- Access API -->
<script>
  document.getElementById('form').addEventListener('submit', (event) => {
    event.preventDefault();
    let input = document.getElementById('input').value;

    // POST
    const url = 'https:blognorte.tk/api/calculator/create?exp='+input;
    fetch(url, {
        mode: 'no-cors',
        method: 'POST',
        headers: {
            'Accept': 'application/json',
            'Content-Type': 'application/json',
            'Access-Control-Allow-Origin': '*',
            'Access-Control-Allow-Methods': 'POST, GET, PUT, DELETE',
            'Access-Control-Allow-Headers': 'application/json',
            'Access-Control-Allow-Credentials': true
        }
    })

    // GET
    fetch("https://blognorte.tk/api/calculator", {
      method: 'GET',
      mode: 'no-cors',
      headers: {
        'Accept': 'application/json',
        'Content-Type': 'application/json',
        'Access-Control-Allow-Origin': '*',
        'Access-Control-Allow-Methods': 'POST, GET, PUT, DELETE',
        'Access-Control-Allow-Headers': 'application/json',
        'Access-Control-Allow-Credentials': true
      }})
      .then(response => response.json())
      .then(data => {
        const table = document.getElementById('table');
        const row = table.insertRow(-1);
        const inputCell = row.insertCell(0);
        const tokensCell = row.insertCell(1);
        const postfixCell = row.insertCell(2);
        const resultCell = row.insertCell(3);
        // Print data to table
        inputCell.innerHTML = data.expression;
        tokensCell.innerHTML = data.tokens;
        rpnCell.innerHTML = data.reverse_polish;
        resultCell.innerHTML = data.result;
      });
  });
</script>