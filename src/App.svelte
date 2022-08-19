<script>
  let firstName = "this";
  let middleName = ".";
  let lastName = "me";
  let beltColour = "black";

  // reactive values % statements
  $: fullName = `${firstName}${middleName}${lastName}`;
  $: console.log(beltColour);
  $: {
    console.log(beltColour);
    console.log(fullName);
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
</script>

<main>
  <!-- link to project lessons :- https://www.youtube.com/watch?v=QJJjXRIg7kI&list=PL4cUxeGkcC9hlbrVO_2QFVqVPhlZmz7tO&index=5 -->

  <h1 style="color:{beltColour}">Hello {fullName}!</h1>
  <!-- dynamic inline style -->
  <!-- <p style="color:{beltColour}">{beltColour} belt</p> -->
  <p style="color:{beltColour}">{fullName} - {beltColour} belt</p>
  <!-- <button on:click={handleClick}>update belt colour</button> -->
  <input type="text" bind:value={firstName} />
  <input type="text" bind:value={middleName} />
  <input type="text" bind:value={lastName} />
  <!-- 1B. 2 way binding --- 2 ways -->
  <!-- <input type="text" on:input={handleInput} value = {beltColour}> -->
  <!-- short method of 2 way binding-->
  <input type="text" bind:value={beltColour} />

  {#each people as person (person.id)}
    <div>
      <h4 on:click={() => handleDelete(person.id)}>{person.name}</h4>
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

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
