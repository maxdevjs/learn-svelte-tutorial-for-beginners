<script>
	import Header from './components/Header.svelte';
	import Footer from './components/Footer.svelte';
	import CreatePollForm from './components/CreatePollForm.svelte'
	import PollList from './components/PollList.svelte'
	import Tabs from './shared/Tabs.svelte';

	// tabs
	let items = ['Current Polls', 'Add New Poll'];
	let activeItem = 'Current Polls';

	const tabChange = (e) => {
		console.log(e);
		console.log(e.type);
		activeItem = e.detail;
	}

	let polls = [
		{
			id: 1,
			question: 'Python or JavaScript',
			answerA: 'Python',
			answerB: 'JavaScript',
			votesA: 9,
			votesB: 15
		}
	];

	const addHandle = (e) => {
		const poll = e.detail;
		polls = [poll, ...polls];
		activeItem = 'Current Polls';
		console.log(polls);
	}
</script>

<Header />
<main>
	<Tabs {activeItem} {items} on:tabChange={tabChange} />
	{#if activeItem === 'Current Polls'}
		<PollList {polls} />
	{:else if activeItem === 'Add New Poll'}
		<CreatePollForm on:add={addHandle} />
	{/if}
</main>
<Footer />

<style>
	main {
		max-width: 960px;
		margin: 40px auto;
	}
</style>