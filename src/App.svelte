<script>
  import Modal from './modal.svelte';

  let showModal = false;

  let firstName, middleName, lastName, age, beltColour;

  // reactive values % statements
 
  $: fullName = `${firstName} ${middleName} ${lastName}`;
  //$: console.log(beltColour);
  $: {
    //console.log(beltColour);
    //console.log(people);
  }
  
const toggleModal= ()=> {
  showModal = !showModal
}

  const handleClick = () => {
    beltColour = "orange";
  };

  // 1A. 2 way binding --- if using on:click method tp call this handleInput function
  //const handleInput = e => {
  //  beltColour = e.target.value;
  // };
  let people = [
    { name: "colette", beltColour: "green", age: 0.4, id: 1 },
    { name: "reuben", beltColour: "orange", age: 1, id: 2 },
    { name: "minx", beltColour: "black", age: 5, id: 3 },
    { name: "mo", beltColour: "black", age: 8, id: 4 },
  ];

  const handleDelete = id => {
    people = people.filter(person => person.id != id);
  };

  const handleAddPerson = () => {
    if (firstName && age && beltColour){
   
    people = [
      ...people,
      { name: firstName, beltColour, age: age, id: people[people.length -1].id +1 },
    ];
  }
  };
  
  const handleClearInputs = () => {
    firstName = null;
    middleName = null;
    lastName=null;
    age=null;
    beltColour=null
  }
 
</script>

<Modal message= "hey, I'm a prop!" {showModal} on:click={toggleModal}/>

<main>
  <!-- link to project lessons :- https://www.youtube.com/watch?v=QJJjXRIg7kI&list=PL4cUxeGkcC9hlbrVO_2QFVqVPhlZmz7tO&index=5 -->
<button on:click|once={toggleModal}>open modal</button>
  <h1 style="color:{beltColour}">Hello {#if !middleName && firstName && lastName}{firstName} {lastName}!{:else if firstName && middleName && lastName} {fullName}! {:else} what's your name?{/if}</h1>
  <!-- dynamic inline style -->
  <!-- <p style="color:{beltColour}">{beltColour} belt</p> -->
  {#if beltColour && firstName && lastName}
  <p style="color:{beltColour}">{fullName} - {beltColour} belt</p>
  {/if}
  
  <!-- <button on:click={handleClick}>update belt colour</button> -->
  <input type="text" placeholder='enter first name' bind:value={firstName} />
  <input type="text" placeholder='enter middle name' bind:value={middleName} />
  <input type="text" placeholder='enter last name' bind:value={lastName} />
  <input type="text" placeholder='enter age' bind:value={age}>
  <!-- 1B. 2 way binding --- 2 ways -->
  <!-- <input type="text" on:input={handleInput} value = {beltColour}> -->
  <!-- short method of 2 way binding-->
  <input type="text" placeholder='enter belt colour' bind:value={beltColour} />
  <div>
  <button on:click={handleAddPerson}>add person</button>
  <button on:click={handleClearInputs}>clear input</button>
</div>
  {#each people as person (person.id)}
    <div>
      <h4 on:click={() => handleDelete(person.id)}>{person.name}</h4>
      {#if person.beltColour === 'black'}
      <p style='color: blue'><strong> MASTER NINJA!</strong></p>
      {/if}
      <p>{person.age} years old, {person.beltColour} belt</p>
      ----------------------------
    </div>
  {:else}
    <p>there are no people to show...</p>
  {/each}
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  h4 {
    cursor: pointer;
  }

  button {
    cursor:pointer
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
