<script>
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  export let name;
  export let goals;
  export let position;
  let showControls = false;

  const addPoint = () => (goals += 1);
  const removePoint = () => (goals -= 1);
  const toggleControls = () => (showControls = !showControls);
  const onDelete = () => dispatch("removeplayer", name);
</script>

<style>
  h1 {
    color: #204f6e;
    font-size: 25px;
  }

  h3 {
    margin-bottom: 10px;
  }
</style>

<div class="card">
  <h1>
    {name}
    <span>
      <button class="btn btn-sm" on:click={toggleControls}>
        {#if showControls}-{:else}+{/if}
      </button>
      <button class="btn btn-danger btn-sm" on:click={onDelete}>x</button>
    </span>
  </h1>
  <h4>Goals Scored: {goals}</h4>
  <h5>Position: {position}</h5>
  {#if showControls}
    <button class="btn" on:click={addPoint}>+1</button>
    <button class="btn btn-dark" on:click={removePoint}>-1</button>
    <input type="number" bind:value={goals} />
  {/if}
</div>
