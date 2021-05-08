<script>
  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();
  export let name;
  export let points;
  let showControl = false;

  function addPoint() {
		points += 1;
	}

  function removePoint() {
		points += 1;
	}

  function removePlayer() {
    dispatch('removePlayer', name);
  }

  function toggleControl() {
    showControl = !showControl;
  }
</script>

<div class="card">
  <h1>{name}
    <button class="btn btn-sm" on:click="{toggleControl}">
      {#if showControl}-{:else}+{/if}
    </button>
    <button class="btn btn-sm" on:click="{removePlayer}">
      &#x2715
    </button>
  </h1>
  <h3>{points}</h3>
  {#if showControl}
    <button class="btn" on:click="{addPoint}">+1</button>
    <button class="btn btn-dark" on:click="{removePoint}">-1</button>
    <input type="number" bind:value="{points}">
  {/if}
</div>

<style>
	h1 { color: #204f6e; }
  h3 { margin-bottom: 10px;}
</style>