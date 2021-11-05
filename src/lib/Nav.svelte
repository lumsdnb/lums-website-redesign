<script>
	import { each } from 'svelte/internal';
	import { page } from '$app/stores';
	import Clothing from '$lib/clothing.svelte';
	import MediaQuery from 'svelte-media-query';

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

	let showMobileMenu = false;

	const handleMobileIconClick = () => (showMobileMenu = !showMobileMenu);
</script>

<nav>
	<MediaQuery query="(min-width: 583px)" let:matches>
		{#if matches}
			<ul class="desktop-nav">
				{#each tabs as tab, i}
					<li
						class={$page.path == tab[0] ? 'active-tab' : 'inactive-tab'}
						on:click={(i) => setActiveTab(i)}
					>
						<a sveltekit:prefetch href={tab[0]}>{tab[1]}</a>
					</li>
				{/each}
			</ul>
		{:else}
			<ul class="mobile-nav">
				<li><a href="/">lums.io</a></li>
				<li class="hamburger-icon" on:click={handleMobileIconClick}>☰</li>
			</ul>
			<ul class="mobile-nav-foldout">
				{#if showMobileMenu}
					{#each tabs as tab, i}
						{#if i !== 0}
							<li
								class={$page.path == tab[0] ? 'active-tab' : 'inactive-tab'}
								on:click={(i) => {
									setActiveTab(i);
									handleMobileIconClick;
								}}
							>
								<a sveltekit:prefetch href={tab[0]}>{tab[1]}</a>
							</li>
						{/if}
					{/each}
				{/if}
			</ul>
		{/if}
	</MediaQuery>
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
	.desktop-nav {
		list-style: none;
		display: flex;
		flex-direction: row;
		justify-content: space-around;
	}
	.mobile-nav {
		list-style: none;
		display: flex;
		flex-direction: row;
		justify-content: flex-end;
		flex-wrap: wrap;
	}
	.mobile-nav-foldout {
		list-style: none;
		display: flex;
		justify-content: flex-end;
		text-align: right;
		padding-right: 3rem;
		flex-wrap: wrap;
		flex-direction: column;
	}

	.hamburger-icon {
		user-select: none;
	}
	ul > li {
		flex: 1;
		height: 100%;
	}
	.mobile-nav > :nth-child(1) {
		color: #000;
		flex: 2;
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
