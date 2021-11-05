<script>
	import { each } from 'svelte/internal';
	import { page } from '$app/stores';
	import Clothing from '$lib/clothing.svelte';

	let tabs = [
		['/', 'lums.io'],
		['/projects', '{case studies}'],
		['/music', '{music}'],
		['/blog', '{blog}'],
		['/wardrobe', '{wardrobe}'],
		['/about', '{about}']
	];
	let activeTab = 0;
	const setActiveTab = (t) => {
		activeTab = t;
	};
</script>

<nav>
	<ul>
		{#each tabs as tab, i}
			<li
				class={$page.path == tab[0] ? 'active-tab' : 'inactive-tab'}
				on:click={(i) => setActiveTab(i)}
			>
				<a sveltekit:prefetch href={tab[0]}>{tab[1]}</a>
			</li>
		{/each}
	</ul>
</nav>

<style>
	nav {
		padding: 0.5rem 0;
		background-color: #fcfcfc;
		color: #232323;
		position: relative;
		top: 0;
		width: 100%;
		text-align: center;
	}
	ul {
		list-style: none;
		display: flex;
		flex-direction: row;
		justify-content: space-around;
	}
	ul > li {
		flex: 1;
		height: 100%;
	}
	ul > :nth-child(1) {
		color: #000;
		flex: 4;
		text-align: left;
	}
	a {
		color: #000;
		text-decoration: none;
	}
	.inactive-tab {
		color: #000;
		text-decoration: none;
		opacity: 0.6;
	}
	.active-tab {
		opacity: 1;
		text-decoration: underline;
		text-decoration-thickness: 1.5px;
		text-underline-offset: 5px;
	}
</style>
