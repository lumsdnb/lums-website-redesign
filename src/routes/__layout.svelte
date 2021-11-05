<script>
	import Nav from '$lib/Nav.svelte';
	import Footer from '$lib/Footer.svelte';
</script>

<svelte:head>
	<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Quantico" />
</svelte:head>

<div class="app-wrapper">
	<Nav />
	<div class="main-content">
		<slot />
	</div>
	<Footer />
</div>

<style>
	.main-content {
		padding: 0 2rem;
	}
	.app-wrapper {
		font-family: Quantico;
	}
</style>
