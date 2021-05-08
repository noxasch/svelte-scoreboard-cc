<script>
  import { createEventDispatcher } from 'svelte';

  const dispatch = createEventDispatcher();

  function onSubmit(event) {
    // console.log(event);
    event.preventDefault();
    dispatch('addPlayer', player);
    player = {
      name: "",
      points: 0
    }
  }

  export let player = {
    name: "",
    points: 0
  }
</script>

<form class="grid-3" on:submit="{onSubmit}">
  <input type="text" placeholder="Player Name" bind:value="{player.name}">
  <input type="number" placeholder="Player points" bind:value="{player.points}">
  <input type="submit" class="btn btn-primary" value="Add Player">
</form>