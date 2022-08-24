<script>
  import { createEventDispatcher } from "svelte";

  let dispatch = createEventDispatcher();

  let name, beltColour, age;
  let skills = [];

  const handleSubmit = () => {
    const person = {
      name,
      beltColour,
      age,
      skills,
      id: Math.random(),
    };
    dispatch("addPerson", person);
  };
</script>

<form on:submit|preventDefault={handleSubmit}>
  <input type="text" placeholder="name" bind:value={name} />
  <input type="number" placeholder="age" bind:value={age} />
  <label for="">skills:</label>
  <input type="checkbox" bind:group={skills} value="fighting" /> fighting<br />
  <input type="checkbox" bind:group={skills} value="sneaking" /> sneaking<br />
  <input type="checkbox" bind:group={skills} value="running" /> running<br />
  <label for="">Belt Colour: </label>
  <select name="" id="" bind:value={beltColour}>
    <option value="black">black</option>
    <option value="orange">orange</option>
    <option value="green">green</option>
  </select>
  <button>Add Ninja</button>
</form>

<style>
</style>
