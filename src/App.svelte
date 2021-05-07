<script>
  let firstNaame = "";
  let lastName = "";
  let src = "favicon.png";
  //let count = 0;

  /*
  const incrementCounter = () => {
    count += 1;
  };

  const handleInput = (event) => {
    name = event.target.value;
  };
  */

  /*
  const resetName = () => {
    name = "Unknown";
  };
  */
  $: fullName = `${firstNaame} ${lastName}`;
  //$: console.log(lastName);
  $: {
    console.log(firstNaame);
    console.log(lastName);
  }

  let fruits = [
    { name: "Apple", color: "Red", amount: 5, id: 1 },
    { name: "Lemon", color: "Yellow", amount: 8, id: 2 },
    { name: "Pear", color: "Green", amount: 12, id: 3 },
  ];

  const deleteFruit = (id) => {
    fruits = fruits.filter((fruit) => fruit.id != id);
  };
</script>

<main>
  <!--
  <h1>Hello {fullName}</h1>
  <h3>Counter: {count}</h3>
  <button on:click={incrementCounter}>Increase counter </button>
  <label for="firstName">First Name</label>
  <input type="text" bind:value={firstNaame} />
  <label for="lastName">Last Name</label>
  <input type="text" bind:value={lastName} />
  <button on:click={resetName}>Set name to unknown</button> 		
  <img {src} alt="Svelte Logo" />
   -->
  <div class="card">
    {#each fruits as fruit (fruit.id)}
      <div class="card">
        <h5>{fruit.name}</h5>
        <p>{fruit.color}</p>
        <button
          on:click={() => {
            deleteFruit(fruit.id);
          }}>Delete</button
        >
      </div>
    {:else}
      <p>There was no fruit found.</p>
    {/each}
  </div>
</main>

<style>
  h5,
  p {
    margin: 4px 0px;
  }

  .card {
    min-width: 400px;
    padding: 8px;
    border-radius: 20px;
    border: 2px solid gray;
    margin-top: 8px;
  }

  main {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  h1 {
    font-size: 72px;
    text-align: center;
  }

  h3 {
    font-size: 38px;
  }
</style>
