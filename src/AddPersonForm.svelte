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
  <!-- svelte-ignore a11y-autofocus -->
  <input type="text" placeholder="name" bind:value={name} autofocus/>
  <input type="number" placeholder="age" bind:value={age} min="0" max="99" />
  <div class="skills">
    <label for="">skills:</label>

    <input class="skill" type="checkbox" bind:group={skills} value="fighting" />
    fighting
    <input class="skill" type="checkbox" bind:group={skills} value="sneaking" />
    sneaking
    <input class="skill" type="checkbox" bind:group={skills} value="running" />
    running
  </div>
  <label for="">Belt Colour: </label>
  <select class="btn" name="" id="" bind:value={beltColour}>
    <option value="black">black</option>
    <option value="brown">brown</option>
    <option value="orange">orange</option>
    <option value="yellow">yellow</option>
    <option value="green">green</option>
    <option value="white">white</option>
  </select><br />
  <button class="btn">Add Ninja</button>
</form>

<style>
  .skills {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .skill {
    display: flex;
    justify-content: space-around;
    margin: 10px 4px 10px 20px;
  }

  .btn {
    width: 50%;
    text-align: center;
  }
</style>
