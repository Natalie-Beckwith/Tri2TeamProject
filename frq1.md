# FRQ1 - Calendar

<div class="calendar">
    <form id="form">
    <label for="year1">Enter the first year:</label><br>
    <input type="text" id="year1" name="year1"><br>
    <label for="year2">Enter the second year:</label><br>
    <input type="text" id="year2" name="year2"><br>
    <button type="submit" id="submit-button">Submit</button>
    <p id="result"></p>
    </form>
    <div>
        <p></p>
    </div>
 </div>

<script>
  document.getElementById('form').addEventListener('submit', (event) => {
  event.preventDefault();

    let year1 = document.getElementById("year1").value;
    let year2 = document.getElementById("year2").value;
    console.log(year1);
    console.log(year2);

    const url = `https://blognorte.tk/api/calendar/numberOfLeapYears/${year1}/${year2}`;
    fetch(url, {method: 'POST', headers:{"Accept":"application/json"}})
      .then(response => response.json())
      .then(data =>
      {
        console.log(data);
        document.getElementById("result").innerHTML = `${data.numberOfLeapYears}`;
      });
  
  }
  );

</script>
