<script>
	import AddPlayer from "./AddPlayer.svelte";
	import Card from "./Card.svelte";
	import Navbar from "./Navbar.svelte";

	// let name = 'John Doe';
	// let points = 1000;
	let players = [
		{
			name: "John Doe",
			points: 53
		},
		{
			name: "Sam Smith",
			points: 45
		},
		{
			name: "Sara William",
			points: 34
		}
	];

	function addPlayer(event) {
		players[players.length] = event.detail;
	}

	function removePlayer(event) {
		const index = players.findIndex((player) => player.name == event.detail);
		players.splice(index, 1);
		players = players;
	}
</script>

<Navbar />
<main class="container">
	<AddPlayer on:addPlayer={addPlayer} />
	{#each players as player}
		<Card {...player} on:removePlayer={removePlayer} />
	{:else}
		<p>No Players</p>
	{/each}
</main>


