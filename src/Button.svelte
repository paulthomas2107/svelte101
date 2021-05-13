<script>
  export let btnText = "Component Button";
</script>

<div on:click>
  <span>Click to log</span>
  <button>{btnText}</button>
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
</style>
