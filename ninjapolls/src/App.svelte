<script>
	import Header from './components/Header.svelte';
	import Footer from './components/Footer.svelte';

	// tabs
	let items = ['Current Polls', 'Add New Poll'];
	let activeItem = 'Current Polls';
</script>

<Header />
<main>
	<p>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Eos at necessitatibus consequuntur praesentium asperiores consequatur nam corrupti. Dolorum dignissimos iusto, repudiandae qui culpa eos quod, nulla eligendi id sed odio.</p>
</main>
<Footer />

<style>
	main {
		max-width: 960px;
		margin: 40px auto;
	}
</style>