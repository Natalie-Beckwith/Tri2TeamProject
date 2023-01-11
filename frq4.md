# FRQ4 - LightBoard

<label for="input">Rows:</label><br />
<input type="text" id="row" name="row" /><br />
<label for="input">Columns:</label><br />
<input type="text" id="col" name="col" /><br />
<label for="input">DiffColor:</label><br />
<input type="text" id="dc" name="dc" /><br />

<!--button type="submit" id="submit-button" action="fetchData()">Generate</button-->
<button onclick="fetchData()">Generate</button>

<table>
  <thead>
    <tr>
      <th>"Light On"</th>
      <th>"Row"</th>
      <th>"Col"</th>
    </tr>
</thead>
<tbody id="ref1">
</tbody>
</table>


<script>
 
 function fetchData()
 {
    const rows = document.getElementById('row').value;
    const cols = document.getElementById('col').value;
    const dc = document.getElementById('dc').value;
    //var button = document.createElement('BUTTON');
    

const url = 'https://blognorte.tk/api/LightBoard/makeBoard';
//const url = 'http://localhost:8085/api/LightBoard/makeBoard';
  //?rows='+rows+'&columms='+cols+'&diffcolor='+dc;
  alert(rows);

    fetch(url, {
      method: 'POST',
      body: JSON.stringify({
        rows: ${rows},
        columns: ${cols},
        diffcolor: ${dc}
      }),
      headers: {
        "Content-type":"application/json; charset=UTF-8"
      }
        })
        .then(response => response.json())
        .then(json => console.log(json));
        
        getLightBoard();
        
  }

function getLightBoard() 
{
  
    const url1 = 'https://blognorte.tk/api/LightBoard/';
    const resultContainer  = document.getElementById("ref1");

    fetch(url1)
    .then(res => res.json())
  .then((out) => {

    alert("Waiting for data..........");

     for (const rs of out.data)
  {
      const tr = document.createElement("tr");
      const n1 = document.createElement("td");
      const n2 = document.createElement("td");
      const n3 = document.createElement("td");
      n1.innerHTML = rs.LightOn;
      n2.innerHTML = rs.row;
      n3.innerHTML = rs.column;
      tr.appendChild(n1);
      tr.appendChild(n2);
      tr.appendChild(n3);
      resultContainer.appendChild(tr);
  }

  })
.catch(err => { throw err });

}

</script>