<script>
  import { createEventDispatcher } from 'svelte';

  let dispatch = createEventDispatcher();

  let name;
  let beltColour;
  let age;
  // let fighting = false;
  // let sneaking = false;
  // let running = false;

  let skills = [];

  const handleSubmit = () => {
    const person = {
      name,
      beltColour,
      age,
      skills,
      id: Math.random()
    };
    dispatch('addPerson', person);
  };
</script>

<form on:submit|preventDefault={handleSubmit}>
    <!-- (label[for=]+input[id=][placeholder=])*{} -->
    <label for="name">Name:</label>
    <input type="text" id="name" placeholder="Name" bind:value={name}>

    <label for="age">Age:</label>
    <input type="number" id="age" placeholder="Age" bind:value={age}>

    <label>Skills:</label>
    <input type="checkbox" bind:group={skills} value="fighting">fighting<br>
    <input type="checkbox" bind:group={skills} value="sneaking">sneaking<br>
    <input type="checkbox" bind:group={skills} value="running">running<br>

    <label>Belt Colour:</label>
    <select bind:value={beltColour}>
      <option value="black">black</option>
      <option value="orange">orange</option>
      <option value="brown">brown</option>
      <option value="white">white</option>
    </select>

    <button>Add Master</button>
  </form>

  <style>
  </style>