<script>
	import '$lib/styles/main.scss';
	import Navbar from './Navbar.svelte';
	import Footer from './Footer.svelte';
</script>

<div class="container">
	<Navbar />
	<main>
		<slot />
	</main>
	<Footer />
</div>

<style scoped lang="scss">
	.container {
		display: grid;
		grid-template-rows: auto 1fr auto;
		height: 100%;
		margin-inline: auto;
		max-inline-size: 1080px;
		padding-inline: 2rem;

		@media (min-width: 1080px) {
			padding-inline: 0;
		}
	}
</style>
