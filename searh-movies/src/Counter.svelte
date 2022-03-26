<script>
    export let initialCounter = 0;
    let contador = initialCounter;
  
    const handleClic = () => {
      contador++;
    };
  </script>
  
  <main>
    <span>{contador}</span>
  </main>
  
  <button on:click={handleClic}>Incrementar</button>
  
  <style>
    main {
      text-align: center;
      padding: 1em;
      max-width: 240px;
      margin: 0 auto;
    }
  
    span {
      color: #ff3e00;
      text-transform: uppercase;
      font-size: 4em;
      font-weight: 100;
    }
  
    @media (min-width: 640px) {
      main {
        max-width: none;
      }
    }
  </style>
  