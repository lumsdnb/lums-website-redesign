<script>
	import Clothing from '$lib/clothing.svelte';
</script>

<svelte:head>
	<title>wardrobe</title>
</svelte:head>

<h1 class="text-5xl">digital wardrobe</h1>

<svelte:component this={Clothing} />
