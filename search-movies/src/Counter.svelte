<script>
  export let initialCounter = 0;
  export let maxCounter = 9;

  let contador = initialCounter;

  const handleClic = () => {
    contador++;
  };

  $: isEvenOrOdd = contador % 2 === 0 ? 'Is even' : 'Is odd';
  $: if (contador > maxCounter) {
    console.log('limit contador');
    contador = maxCounter;
  }
</script>

<main>
  <span>{contador}</span>
  <span>{isEvenOrOdd}</span>
  <!-- <span>{contador % 2 === 0 ? 'Is even' : 'Is odd'}</span> -->
</main>

<button on:click={handleClic}>Incrementar</button>

<style>
  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
