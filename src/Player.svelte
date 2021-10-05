<script>
  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();

  export let name;
	export let points;
  let editPoints = false;

	const handleClick = () => editPoints = !editPoints;
	const addPoints = () => points += 1;
	const removePoints = () => points -= 1;
  const onDelete = (e) => dispatch('removeplayer', name);
  
</script>

<div classname='player-card'>
  <h2>
    {name}
    <button on:click={handleClick}>
      {#if !editPoints}+{:else}-{/if}
    </button>
    <button class='danger' on:click={onDelete}>x</button>
  </h2>
  {#if editPoints}
    <input type='text' bind:value={points}/>
    <button on:click={removePoints}>-</button>
    <button on:click={addPoints}>+</button>
  {/if}
  <p>Points: {points}</p>
</div>

<style>
	div {
		border: 1px black solid;
		margin-top: 1em;
	}
	p {
		font-size: medium;
	}
  button {
    font-size: small;
  }
  .danger {
    background-color: red;
  }
</style>