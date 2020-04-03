<script>
  let name = "Teq";
  let beltColour = "black";

  const handleClick = () => {
    beltColour = "orange";
  };

  const handleInput = e => {
    beltColour = e.target.value;
  };
</script>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
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

<main>
  <h1>Hello {name}!</h1>
  <p on:click={handleClick} style="color: {beltColour}">{beltColour} belt</p>
  <!-- <input
    type="text"
    on:input={handleInput}
    value={beltColour}
    onfocus="this.select();" /> -->
  <input type="text" bind:value={beltColour} onfocus="this.select();" />
  <button on:click={handleClick}>update belt color</button>
</main>
