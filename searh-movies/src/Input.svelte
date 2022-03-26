<script>
  let value = '';
  let response = [];

  const handleInput = (event) => (value = event.target.value);

  $: if (value.length > 2) {
    fetch(`http://www.omdbapi.com/?apikey=168dd179&s=${value}`)
      .then((res) => res.json())
      .then((apiResponse) => {
        response = apiResponse.Search
        console.log(apiResponse);
      });
  }
</script>

<style>
  input {
    display: flex;
    justify-content: center;
    align-items: center;
  }
</style>

<input {value} on:input={handleInput} type="text" />
