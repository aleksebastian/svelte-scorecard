<script>
	import Nav from './Navbar.svelte';
	import AddPlayer from './AddPlayer.svelte';
	import Player from './Player.svelte';

	let players = [
		{
			name: 'John Doe',
			points: 43
		},
		{
			name: 'Jane Doe',
			points: 56
		},
		{
			name: 'Rocco',
			points: 560
		}
	]

	const addPlayer = (e) => {
		const newPlayer = e.detail;
		players = [newPlayer, ...players];
	}
	const removePlayer = (e) => {
		const nameOfPlayerToRemove = e.detail;
		players = players.filter((player) => player.name !== nameOfPlayerToRemove);
	}
</script>

<main>
	<Nav />
	<AddPlayer on:addplayer={addPlayer}/>
	{#if players.length}
		{#each players as player}
			<Player name={player.name} points={player.points} on:removeplayer={removePlayer}/>
		{/each}
	{:else}
		<h2>No players.</h2>
	{/if}
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		/* max-width: 240px; */
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>