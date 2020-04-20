<script>
  let name;
  let beltColour;
  let age;
  let fighting = false;
  let sneaking = false;
  let running = false;

  const handleSubmit = () => {
    console.log(name, beltColour, age, fighting, sneaking, running);
  }
</script>

<form on:submit|preventDefault={handleSubmit}>
    <!-- (label[for=]+input[id=][placeholder=])*{} -->
    <label for="name">Name:</label>
    <input type="text" id="name" placeholder="Name" bind:value={name}>

    <label for="belt">Belt:</label>
    <input type="text" id="belt" placeholder="Belt Colour" bind:value={beltColour}>

    <label for="age">Age:</label>
    <input type="number" id="age" placeholder="Age" bind:value={age}>

    <label>Skills:</label>
    <input type="checkbox" bind:checked={fighting}>fighting<br>
    <input type="checkbox" bind:checked={sneaking}>sneaking<br>
    <input type="checkbox" bind:checked={running}>running<br>

    <button>Add Master</button>
  </form>

  <style>
  </style>