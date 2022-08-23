  <script>
  import Modal from './Modal.svelte';
  import AddPersonForm from './AddPersonForm.svelte'

  let showModal = false;

  let toggleModal = () => {
    showModal = !showModal;
  };

	let people = [
    { name: "colette", beltColour: "green", age: 0.4, id: 1 },
    { name: "reuben", beltColour: "orange", age: 1, id: 2 },
    { name: "minx", beltColour: "black", age: 5, id: 3 },
    { name: "mo", beltColour: "black", age: 8, id: 4 },
  ];

  const handleClick = (e, id) => {
    people = people.filter(person => person.id != id);
    console.log(e);
  };

  const addPerson = (e) => {
console.log(e.detail);
const person = e.detail
people = [person, ...people]
showModal = false;
  }
</script>

<Modal {showModal} on:click={toggleModal}>
  <!-- <h3>Add a New Ninja</h3> -->
  <AddPersonForm on:addPerson={addPerson} />
</Modal>
<main>
  <button on:click={toggleModal}>Open Modal</button>
  {#each people as person (person.id)}
    <div>
      <h4>{person.name}</h4>
      {#if person.beltColour === 'black'}
        <p><strong>MASTER NINJA</strong></p>
      {/if}
      <p>{person.age} years old, {person.beltColour} belt.</p>
      {#if person.skills}
           <label for="">skills: </label>
      {#each person.skills as skill }
      <p>{skill}</p>
      {/each}
     {/if}
        <button on:click={(e) => handleClick(e, person.id)}>delete</button>
    </div>
     {:else}
    <p>There are no people to show...</p>
    
  {/each}
</main>

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