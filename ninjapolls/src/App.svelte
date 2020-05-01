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

	const addHandle = (e) => {
		activeItem = 'Current Polls';
	}

</script>

<Header />
<main>
	<Tabs {activeItem} {items} on:tabChange={tabChange} />
	{#if activeItem === 'Current Polls'}
		<PollList />
	{:else if activeItem === 'Add New Poll'}
		<CreatePollForm on:add={addHandle} />
	{/if}
</main>
<Footer />

<style>
	main {
		user-select: none;
		max-width: 960px;
		margin: 40px auto;
	}
</style>