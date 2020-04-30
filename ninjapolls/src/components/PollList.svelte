<script>
  export let polls = []; 
</script>

<div class="poll-list">
  {#each polls as poll (poll.id)}
    <div>
			{ poll.question }:    

			{ poll.answerA } ({ poll.votesA } votes)    
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