<script>
  import Movie from './Movie.svelte';

  let value = '';
  let loading = false;
  let response = [];

  const handleInput = (event) => (value = event.target.value);

  $: if (value.length > 2) {
    loading = false;
    fetch(`http://www.omdbapi.com/?apikey=168dd179&s=${value}`)
      .then((res) => res.json())
      .then((apiResponse) => {
        response = apiResponse.Search || [];
        loading = false;
      });
  }
</script>

<input {value} on:input={handleInput} placeholder="Search films" type="text" />

{#if loading}
  <strong>Loading...</strong>
{:else}
  {#each response as { Title: movieTitle, Poster: moviePoster, Year: movieYear }}
    <Movie title={movieTitle} poster={moviePoster} year={movieYear} />
  {:else}
    <strong>No hay resultados</strong>
  {/each}
{/if}
