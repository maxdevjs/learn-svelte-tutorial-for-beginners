<script>
  let people = [
    { name: 'Tim', beltColour: 'black', age: 11, id: 1 },
    {name:'Teq',beltColour:'orange',age:8,id:2},
    { name: 'Dudu', beltColour: 'brown', age: 12, id: 3 }
  ];
</script>

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
      <p>{person.age} yo - {person.beltColour} belt</p>
    </div>
  {:else}
    <p>There are no people to show...</p>
  {/each}
</main>