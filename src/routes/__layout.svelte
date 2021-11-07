<!-- 1. Assign current route's path to `key` prop -->
<script context="module">
	export const load = async ({ page }) => ({
		props: {
			key: page.path
		}
	});
</script>

<script>
	import '../app.css';
	import Nav from '$lib/Nav.svelte';
	import Footer from '$lib/Footer.svelte';
	import PageTransition from '$lib/PageTransition.svelte';
	export let key;
</script>

<div class="app-wrapper">
	<Nav />
	<main class="main-content px-20 py-7">
		<PageTransition refresh={key}>
			<slot />
		</PageTransition>
	</main>
	<Footer />
</div>

<style>
	.main-content {
		height: 90vh;
	}
	.app-wrapper {
		font-family: Quantico;
	}
</style>
