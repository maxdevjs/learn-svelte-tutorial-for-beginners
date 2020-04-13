<script>
  let name;
  let beltColour;
  let age;

  const handleSubmit = () => {
    console.log(name, beltColour, age);
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

    <button>Add Master</button>
  </form>

  <style>
  </style>