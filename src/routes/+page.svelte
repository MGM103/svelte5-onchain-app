<script>
	import { onMount } from 'svelte';
	import { fade } from 'svelte/transition';
	import { typewriter } from '$lib';

	// STATE VARS
	let landingPageVisible = false;

	// LIFECYCLE LOGIC
	onMount(() => {
		landingPageVisible = true;
		window.scrollTo(0, 0);
	});
</script>

<div id="landing-container">
	<section id="landing-section">
		{#if landingPageVisible}
			<h1 in:fade={{ delay: 100, duration: 1000 }}>Go</h1>
			<h1 in:fade={{ delay: 800, duration: 1000 }}>Fund</h1>
			<h1 in:fade={{ delay: 1500, duration: 1000 }}>Yourself.</h1>

			<button in:fade={{ delay: 2200, duration: 1000 }} class="shadow-btn">Raise funds</button>
			<p in:typewriter={{ speed: 2, delay: 2250 }}>
				Harness the power of crowd-sourced fundraising today
			</p>
		{/if}
	</section>
</div>

<style scoped lang="scss">
	#landing-section {
		align-items: center;
		display: flex;
		flex-direction: column;
		justify-content: center;
		margin-top: 60px;
		padding: 2.5rem;
		position: relative;

		h1 {
			font-size: 108px;
			margin: 0;
		}

		button {
			margin-top: 5rem;
		}

		p {
			margin-top: 1rem;
		}
	}
</style>
