<script>
  import { createEventDispatcher } from "svelte";
  export let name;
  export let points;
  const dispatch = createEventDispatcher();
  const addPoint = () => (points += 1);
  const removePoint = () => (points -= 1);
  const toggleControls = () => (showControls = !showControls);
  let showControls = false;

  const handleDelete = () => dispatch("removeplayer", name);
</script>

<style>
  h1 {
    color: #204f6e;
  }

  h2 {
    margin-bottom: 20px;
  }
</style>

<div class="card">
  <h1>{name}</h1>
  <h2>{points}</h2>
  <button class="btn btn-sm" on:click={toggleControls}>
    {#if showControls}hide{:else}show{/if}
  </button>
  {#if showControls}
    <button class="btn" on:click={addPoint}>+1</button>
    <button class="btn btn-dark" on:click={removePoint}>-1</button>
    <input type="number" bind:value={points} />
  {/if}
  <button class="btn btn-danger" on:click={handleDelete}>Delete</button>
</div>
