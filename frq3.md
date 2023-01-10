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
  const url = 'https://blognorte.tk/api/calculator/create?exp='+input;
  fetch(url, {method: 'POST', headers:{"Accept":"application/json"}, mode: 'no-cors'})
  .then(response => response.text())
  .then(data => {
      console.log(data);
      console.log("make table");
      const table = document.getElementById('table');
      const row = table.insertRow(-1);
      const inputCell = row.insertCell(0);
      const tokensCell = row.insertCell(1);
      const postfixCell = row.insertCell(2);
      const resultCell = row.insertCell(3);
      console.log("tables done");
      // Print data to table
      console.log("begin output data");
      console.log("expression");
      inputCell.innerHTML = data.expression;
      console.log("tokens");
      tokensCell.innerHTML = data.tokens;
      console.log("postfix");
      rpnCell.innerHTML = data.reverse_polish;
      console.log("output data");
      resultCell.innerHTML = data.result;
      console.log("data outputted");
    });
  }
  );
</script>