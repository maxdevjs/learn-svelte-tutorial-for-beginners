<script>
  // import { onMount, onDestroy } from 'svelte';
  import { fade, slide, scale } from 'svelte/transition';
  import { flip } from 'svelte/animate';
  import PollStore from '../stores/PollStore.js';
  import PollDetails from './PollDetails.svelte';

  // export let polls = [];

  // const unsub = PollStore.subscribe(data => {
  //   polls = data;
  // });

  // onMount(() => {
  //   // data from db?
  //   console.log('component mounted');
  // });

  // onDestroy(() => {
  //   // unsub from store
  //   unsub();
  //   console.log('component destroyed');
  // });
</script>

<div class="poll-list">
  {#each $PollStore as poll (poll.id)}
    <div in:fade out:scale|local animate:flip={{duration: 500}}>
      <PollDetails {poll} />
    </div>
	{/each}
</div>

<style>
  .poll-list {
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-gap: 20px;
  }
</style>