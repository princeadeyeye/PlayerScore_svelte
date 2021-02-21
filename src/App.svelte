<script lang="ts">
	import NavBar from './NavBar.svelte'
	import Player from './Player.svelte'
	import AddPlayer from './AddPlayer.svelte'
	let players = [
		{
			name: 'John Doe',
			points: 15
		},
		{
			name: 'Adeyeye Muiz',
			points: 30
		},
		{
			name: 'Taye Taiwo',
			points: 75
		},
		{
			name: 'Michael Tyson',
			points: 74
		}
	]

	const addPlayer = (e) => {
		const newPlayer = e.detail;
		players=[...players, newPlayer]
	}
	const removePlayer = (e) => {
		const selectedPlayer = e.detail;
		players = players.filter(player => player.name !== selectedPlayer)
	}
</script>
<style>
	
</style>

<div class="container">
	<NavBar />
	{#if players.length === 0}
	<p>Players not available</p>
	{/if}
	{#each players as player }
	<Player on:removeplayer={removePlayer} name={player.name} points={player.points} />
	{/each}
	<AddPlayer on:addPlayer={addPlayer} />
</div>
