<script>
  export let title, poster, year;
</script>

<article>
  <img src={poster} alt={title} />
  <h3>{title}</h3>
  <span>{year}</span>
  {#if 2020 - year < 5}
    <i>🆕</i>
  {/if}
</article>

<style>
  article {
    border: 1px solid #eee;
    border-radius: 4px;
    padding: 1rem;
    padding: 1rem;
  }

  h3 {
    font-size: 24px;
    margin-bottom: 4px;
  }
</style>
