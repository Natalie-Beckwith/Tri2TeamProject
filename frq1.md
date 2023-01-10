# Hello!

<div class="calendar">
    <form action="">
    <label for="year1">Enter the first year:</label><br>
    <input type="text" id="year1" name="year1"><br>
    <label for="year2">Enter the second year:</label><br>
    <input type="text" id="year2" name="year2"><br>
    <input type="submit" value="Submit" onclick="numberOfLeapYears()">
    <p id="result"></p>
    </form>
    <div>
        <p></p>
    </div>
 </div>

<script>
      function numberOfLeapYears()
      {
        let year1 = document.getElementById("year1").value;
        let year2 = document.getElementById("year2").value;
        console.log(year1);
        console.log(year2);
        const url = `https://blognorte.tk/api/calendar/numberOfLeapYears/${year1}/${year2}`;
        fetch(url, {method: 'GET', headers:{"Accept":"application/json"}, mode: 'no-cors'})
          .then((data) => data.json())
          .then((data) =>
          {
            console.log(data);
            document.getElementById("result").innerHTML = `${data.numberOfLeapYears}`;
          });
      }

</script>
