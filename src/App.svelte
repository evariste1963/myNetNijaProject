<script>
  let name = "this.me";
  let beltColour = "black";
  const handleClick = () => {
    beltColour = "orange";
  };
  const handleInput = e => {
    beltColour = e.target.value;
  };
</script>

<main>
  <!-- link to project lessons :- https://www.youtube.com/watch?v=QJJjXRIg7kI&list=PL4cUxeGkcC9hlbrVO_2QFVqVPhlZmz7tO&index=5 -->

  <h1>Hello {name}!</h1>
  <!-- dynamic inline style -->
  <p style="color:{beltColour}">{beltColour} belt</p>
  <button on:click={handleClick}>update belt colour</button>
  <!-- 2 way binding --- 2 ways -->
  <!-- <input on:input={handleInput} type="text" value = {beltColour}> -->
  <!-- short method of 2 way binding-->
  <input type="text" bind:value={beltColour} />
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
