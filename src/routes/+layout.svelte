<script>
	import '$lib/styles/main.scss';
	import Navbar from './Navbar.svelte';
	import Footer from './Footer.svelte';
</script>

<Navbar />
<main>
	<slot />
</main>
<Footer />
