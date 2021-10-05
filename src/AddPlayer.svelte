<script>
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  let player = {
    name: '',
    points: 0
  }
  const handleSubmit = (e) => {
    dispatch('addplayer', player);
    player = {
      name: '',
      points: 0
    }
  }
</script>

<form on:submit|preventDefault={handleSubmit}>
  <input type='text' placeholder="Player name" bind:value={player.name}/>
  <input type='number' placeholder="Points" bind:value={player.points}/>
  <input type='submit' value='+'>
</form>

<style>

</style>