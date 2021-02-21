<script>
    import { createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher()
    let player = {
        name: '',
        points: 0
    }
    const onSubmit = e => {
        e.preventDefault();
        dispatch('addPlayer', player)
        player = { name: '', points: 0 }
    }
</script>
<form class="row g-3" on:submit="{onSubmit}">
    <input type="text" placeholder="Player name" bind:value={player.name} />
    <input type="number" placeholder="Player points" bind:value="{player.points}" />
    <input type="submit" value="Add Player" class="btn btn-primary" />
</form>