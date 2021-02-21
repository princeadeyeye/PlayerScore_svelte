<script lang="ts">
    import { createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher()

	 export let name: string;
	 export let  points: number;
	 let showControls = false;
	 import { CardBody, CardHeader } from 'sveltestrap';
	const addpoint = () => points++
	const removePoint = () => points--
	const toggleControl = () => showControls = !showControls;
    const deletePlayer = (e) => {
        e.preventDefault();
        dispatch('removeplayer', name)
    }
</script>
<style>
	h1 {
		color: #204f6e;
	}
</style>

	<div class="card" style="width: 18rem;">
		<CardHeader>
			<h5>{name}</h5>
		</CardHeader>
		  <CardBody>
			  <h1>
				{points}
				<button on:click={toggleControl} class="btn btn-small">
					{#if showControls}-{:else}+{/if}
				</button>
                <button class="btn btn-danger btn-small" on:click={deletePlayer}>X</button>
			  </h1>
			</CardBody>
		  {#if showControls}
		  <div>
			<button on:click ={addpoint} class="btn btn-secondary btn-sm">+1</button>
		  	<button on:click ={removePoint} class="btn btn-danger btn-sm">-1</button>
		  </div>
			<input type="number" bind:value={points} />
		  {/if}
		</div>
