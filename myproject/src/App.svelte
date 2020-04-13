<script>
  import Modal from './Modal.svelte';

  let people = [
    { name: 'Tim', beltColour: 'black', age: 11, id: 1 },
    {name:'Teq',beltColour:'orange',age:8,id:2},
    { name: 'Dudu', beltColour: 'brown', age: 12, id: 3 }
  ];

  const handleClick = (e, id) => {
    // Check also
    // https://love2dev.com/blog/javascript-remove-from-array/
    people = people.filter((person) => person.id != id);
    console.log(e);
  };

</script>

<Modal />

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>

<main>
  {#each people as person (person.id)}
    <div style="color: {person.beltColour};">
      <h4>{person.name}</h4>
      {#if person.beltColour === 'black'}
        <p><strong>MASTER NINJA</strong></p>
      {:else if person.beltColour === 'orange'}
        <p><u>MASTER OF MASTERS</u></p>
      {:else}
        <p><i>MASTER ANYWAY</i></p>
      {/if}
      <p>{person.age} yo - {person.beltColour} belt</p>
      <button on:click={(e) => handleClick(e, person.id)}>delete</button>
    </div>
  {:else}
    <p>There are no people to show...</p>
  {/each}
</main>