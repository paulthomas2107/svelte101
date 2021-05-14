<script>
  export let btnText = "Component Button";
</script>

<!--<div class="card" on:click|self> -->
<div class="card">
  <span>Click to log</span>
  <button on:click|once>{btnText}</button>
</div>

<main />

<style>
  main {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  button {
    background: #667eea;
    border: 1px solid #4c516f;
    color: #fff;
  }
  .card {
    padding: 12px;
    border: 2px solid gray;
    margin-bottom: 8px;
  }
</style>
