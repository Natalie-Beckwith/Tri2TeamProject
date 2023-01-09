## FRQ 1 - Calendar
<p id="test"></p>

<script>

  function getInput()
  {
      let inputYear = document.getElementById("inputYear").value;
      return inputYear;
  }

  function isLeapYear(yearparam)
  {
      result = document.getElementById("result");

      // Fetch data from API
      fetch('https://blognorte.tk/api/calendar/isLeapYear/' + yearparam + "/")
      .then(response => response.json())
      .then(data =>
      {
          console.log(data);
          result.innerHTML = "Is" + yearparam + " a leap year?: " + data.isLeapYear;
      })
  }

</script>

### Enter any year to see if it's a leap year:
<input class="textbox" id="inputYear" placeholder="Enter a Year">
<button class="submit-button" onclick="isLeapYear(getInput())">Go!</button>
<p id="result"></p>
