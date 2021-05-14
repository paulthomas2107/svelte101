<script>
  import Announcement from "./Announcement.svelte";
  import Button from "./Button.svelte";
  import Card from "./Card.svelte";
  import Form from "./Form.svelte";

  const log = () => {
    console.log("Element Clicked");
  };

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
    { name: "Apple", color: "Red", amount: 4, id: 1 },
    { name: "Lemon", color: "Yellow", amount: 3, id: 2 },
    { name: "Pear", color: "Green", amount: 3, id: 3 },
  ];

  const deleteFruit = (id) => {
    fruits = fruits.filter((fruit) => fruit.id != id);
  };

  let num = 10;
  let name = "Rory";
  let isChecked = true;
  let value = 2;
  let selected;
  let questions = [
    { id: 1, text: "What is your fave color ?" },
    { id: 2, text: "What is your fave fruit ?" },
  ];

  let foods = [
    { name: "Apple", color: "Red", id: 1 },
    { name: "Banana", color: "Yellow", id: 2 },
  ];

  const addFood = (e) => {
    //console.log(e.detail);
    const food = e.detail;
    foods = [food, ...foods];
  };
</script>

{#if num > 10}
  <p>Greaster than 10</p>
{:else if num < 10}
  <p>Less than 10</p>
{:else}
  <p>Equal to 10</p>
{/if}

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

  <Form on:addFood={addFood} />
  {#each foods as food (food.id)}
    <div class="fooditem">
      <h3>{food.name}</h3>
      <p>Color: {food.color}</p>
    </div>
  {/each}

  <input type="text" bind:value={name} />
  <input type="number" bind:value={num} />
  <input type="checkbox" bind:checked={isChecked} />

  <labeL>
    <input type="radio" bind:group={value} value={1} />
    1
  </labeL>
  <labeL>
    <input type="radio" bind:group={value} value={2} />
    2
  </labeL><labeL>
    <input type="radio" bind:group={value} value={3} />
    3
  </labeL>

  <select bind:value={selected}>
    {#each questions as question}
      <option value={question}>
        {question.text}
      </option>
    {/each}
  </select>

  <Card>
    <div>
      <h3>Card</h3>
      <p>This is my name: Paul</p>
    </div>
    <button slot="button">Test Button</button>
    <div>
      <h4>This is below all...</h4>
    </div>
  </Card>
  <Button on:click={log} />
  <button on:click={log}>App button</button>
  <Announcement />
  <div class="alert">This is our alert in main app</div>
  <div class="card">
    {#each fruits as fruit (fruit.id)}
      {#if fruit.amount < 4}
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
        <p>The amount for {fruit.name} is greater than or equal to 4</p>
      {/if}
    {:else}
      <p>There was no fruit found.</p>
    {/each}
  </div>
</main>

<style>
  .fooditem {
    border: 2px solid gray;
    text-align: left;
    padding: 8px;
    margin-top: 20px;
    width: 100%;
  }
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
    align-items: flex-start;
  }

  h3 {
    font-size: 38px;
  }
</style>
