<script>
  import Card from '../shared/Card.svelte';
  import PollStore from '../stores/PollStore.js';
  import Button from '../shared/Button.svelte';
  import { fade, slide, scale } from 'svelte/transition';

  import { tweened } from 'svelte/motion';

  export let poll;

  let borderWidthA;
  let borderWidthB;
  let borderStyleA = 'solid';
  let borderStyleB = 'solid';
  const borderColorA = '#d91b42';
  const borderColorB = '#45c496';
  const oneToSix = `1px 1px 1px 6px`;
  const oneToThree = `1px 1px 1px 3px`;

  const setBorder = () => {
    if (poll.votesA > poll.votesB) {
      borderWidthA = oneToSix;
      borderWidthB = oneToThree;
    } else if (poll.votesA < poll.votesB) {
      borderWidthA = oneToThree;
      borderWidthB = oneToSix;
    } else if (poll.votesA === poll.votesB) {
      borderWidthA = oneToSix;
      borderWidthB = oneToSix;
      if (poll.votesA === 0 ) {
        borderWidthA = oneToSix;
      }
      if (poll.votesB === 0 ) {
        borderWidthB = oneToSix;
      }
    }
  };

  // reactive values
  $: totalVotes = poll.votesA + poll.votesB;
  $: percentA = Math.floor(100 / totalVotes * poll.votesA) || 0;
  $: percentB = Math.floor(100 / totalVotes * poll.votesB) || 0;

  // tweened percentages
  const tweenedPercentageA = tweened(0);
  const tweenedPercentageB = tweened(0);
  $: tweenedPercentageA.set(percentA);
  $: tweenedPercentageB.set(percentB);
  $: console.log($tweenedPercentageA, $tweenedPercentageB);

  // handling votes
  const voteHandle = (option, id) => {
    PollStore.update(currentPolls => {
      let copiedPolls = [...currentPolls];
      let upvotedPoll = copiedPolls.find((poll) => poll.id === id);
      if (option === 'a') {
        upvotedPoll.votesA++;
      }
      if (option === 'b') {
        upvotedPoll.votesB++;
      }
      
      return copiedPolls;
    });

    setBorder();
  };

  setBorder();

  const deletePoll = (id) => {
    PollStore.update(currentPolls => {
      // let copiedPolls = [...currentPolls];
      // // console.log(copiedPolls)
      // let pollToDelete = copiedPolls.find((poll) => poll.id === id);
      // // console.log(pollToDelete);
      // return copiedPolls.filter(p => p.id !== pollToDelete.id);

      return currentPolls.filter(p => p.id !== id);
    });
  };
</script>

<Card>
  <!-- <form on:submit|preventDefault={deletePoll(poll.id)}> -->
  <!-- <form on:submit|preventDefault> -->
    <div class="poll">
      <h3>{ poll.question }</h3>
      <p>Total votes: { totalVotes }</p>
      <div class="answer" on:click={() => voteHandle('a', poll.id)}>
        <div transition:scale class="percent percent-a" style="width:{$tweenedPercentageA}%; border-width: {borderWidthA}; border-color: {borderColorA}; border-style: {borderStyleA};"></div>
        <span>{ poll.answerA } ({ poll.votesA } votes)</span>
      </div>
      <div class="answer" on:click={() => voteHandle('b', poll.id)}>
        <div transition:slide={{direction: 'left'}} class="percent percent-b" style="width: {$tweenedPercentageB}%;
      border-width: {borderWidthB}; border-color: {borderColorB}; border-style: {borderStyleB};"></div>
        <span>{ poll.answerB } ({ poll.votesB } votes)</span>
      </div>
      <div>
      <!-- <div on:click={() => deletePoll(poll.id)}>Delete Poll</div> -->
      <div class="delete">
        <Button flat="true" on:click={() => deletePoll(poll.id)}>Delete Poll</Button>
      </div>
    </div>
  <!-- </form> -->
</Card>

<style>
  h3{
    margin: 0 auto;
    color: #555;
  }
  p{
    margin-top: 6px;
    font-size: 14px;
    color: #aaa;
    margin-bottom: 30px;
  }
  .answer{
    background: #fafafa;
    cursor: pointer;
    margin: 10px auto;
    position: relative;
  }
  .answer:hover{
    opacity: 0.6;
  }
  span{
    display: inline-block;
    padding: 10px 20px;
  }

  .percent {
    height: 100%;
    position: absolute;
    box-sizing: border-box;
  }

  .percent-a {
    /* border-left: 4px solid #d91b42; */
    background: rgba(217, 27, 66, 0.2);
  }

  .percent-b {
    /* border-left: 4px solid #45c496; */
    background: rgba(79, 196, 150, 0.2);
  }

  .delete {
    margin-top: 30px;
    text-align: center; 
  }
</style>