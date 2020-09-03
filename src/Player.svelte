<script>
  import { createEventDispatcher } from 'svelte';

  const dispatch = createEventDispatcher();

  export let name;
  export let points;
  let showControls = false;

  const addPoint = () => (points += 1);
  const removePoint = () => (points -= 1);
  const toggleControls = () => (showControls = !showControls);
  const removePlayer = () => dispatch('removeplayer', name);
</script>

<style>
  .player {
    border: 3px dashed #3d315b;
    margin: 2rem 0;
    padding: 1.25rem;
  }

  h2 {
    display: flex;
    align-items: center;
    font-weight: 400;
    font-size: 2rem;
    line-height: 1;
    margin: 0;
  }

  h2 .btn {
    margin: 0 0.25rem;
  }

  h3 {
    font-weight: 400;
    font-size: 1.7rem;
    line-height: 1;
    margin: 2rem 0;
  }

  input {
    margin: 0;
  }

  input[type='number'] {
    margin-top: 1.5rem;
  }
</style>

<div class="player">
  <h2>
    {name}
    <button class="btn" on:click={toggleControls}>
      {#if showControls}-{:else}+{/if}
    </button>
    <button class="btn btn--danger" on:click={removePlayer}>x</button>
  </h2>
  <h3>Points: {points}</h3>
  {#if showControls}
    <button class="btn" on:click={addPoint}>+1</button>
    <button class="btn" on:click={removePoint}>-1</button>
    <br />
    <input type="number" bind:value={points} />
  {/if}
</div>
