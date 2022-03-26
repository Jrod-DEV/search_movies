<script>
  import Movie from './Movie.svelte';

  let value = '';
  let response = [];

  const handleInput = (event) => (value = event.target.value);

  $: if (value.length > 1) {
    response = fetch(`http://www.omdbapi.com/?apikey=168dd179&s=${value}`)
      .then((res) => {
        if (!res.ok) {
          throw new Error('Something bad happened with the fetching of movies');
        } else {
          return res;
        }
      })
      .then((res) => res.json())
      .then((apiResponse) => apiResponse.Search || []);
  }
</script>

<input {value} on:input={handleInput} placeholder="Search films" type="text" />

{#await response}
  <strong>Loading...</strong>
{:then movies}
  {#each movies as { Title: movieTitle, Poster: moviePoster, Year: movieYear }}
    <Movie title={movieTitle} poster={moviePoster} year={movieYear} />
  {:else}
    <strong>No hay resultados</strong>
  {/each}
{:catch error}
  <p>❌ There has been an error: {error.message}</p>
{/await}
