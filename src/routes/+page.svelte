<script>
	import { onMount } from 'svelte';
	import { fade } from 'svelte/transition';
	import { typewriter } from '$lib';
	import { AidSVG, AnonymousSVG, ChainsSVG, GlobeSVG } from '$lib/assets';

	// STATE VARS
	let landingPageVisible = false;
	let fundRaisingPromoVisible = false;
	let donationPromoVisible = false;
	let fundRaisingContainer;
	let donationContainer;

	const observerOptions = {
		root: null,
		rootMargin: '0px',
		threshold: [0, 0.2, 0.4, 0.6, 0.8, 1]
	};

	// LIFECYCLE LOGIC
	onMount(() => {
		landingPageVisible = true;
		window.scrollTo(0, 0);

		const fundRaisingPromoObserver = new IntersectionObserver(
			renderFundRaisingPromo,
			observerOptions
		);
		const donationPromoObserver = new IntersectionObserver(renderDonationPromo, observerOptions);

		fundRaisingPromoObserver.observe(fundRaisingContainer);
		donationPromoObserver.observe(donationContainer);

		return () => {
			fundRaisingPromoObserver.unobserve(fundRaisingContainer);
			donationPromoObserver.unobserve(donationContainer);
		};
	});

	// UTILITY FUNCTIONS
	const renderFundRaisingPromo = (entries) => {
		const [entry] = entries;

		if (entry.intersectionRatio >= 0.6) {
			fundRaisingPromoVisible = true;
		} else {
			fundRaisingPromoVisible = false;
		}
	};

	const renderDonationPromo = (entries) => {
		const [entry] = entries;

		if (entry.intersectionRatio >= 0.6) {
			donationPromoVisible = true;
		} else {
			donationPromoVisible = false;
		}
	};
</script>

<div id="landing-container">
	<section id="landing-section">
		{#if landingPageVisible}
			<h1 in:fade={{ delay: 100, duration: 1000 }}>Go</h1>
			<h1 in:fade={{ delay: 800, duration: 1000 }}>Fund</h1>
			<h1 in:fade={{ delay: 1500, duration: 1000 }}>Yourself.</h1>

			<button in:fade={{ delay: 2200, duration: 1000 }} class="shadow-btn">Raise funds</button>
			<p in:typewriter={{ delay: 2200 }}>Harness the power of crowd-sourced fundraising today</p>
		{/if}
	</section>
	<section
		bind:this={fundRaisingContainer}
		class={`promo-section ${fundRaisingPromoVisible ? 'fade-in' : 'fade-out'}`}
	>
		<div class="promo-container" transition:fade>
			<div class="promo-card card">
				<h2>Raise funds for a special cause</h2>
				<p>
					This platform allows you to leverage the power of smart contracts on the blockchain to
					raise funds for any type of cause near and dear to your heart in a decentralized and
					permissionless manner.
				</p>
				<p>
					This means that Go Fund Yourself facilitates fund raising that is censorship resistant and
					global in its out-reach. No one can take down your fund-raising initiative and anyone with
					an internet connection can contribute to your cause.
				</p>
				<p>Get started raising today.</p>
				<button class="shadow-btn" on:click={() => goto('/fund-yourself')}>Fund yourself</button>
			</div>
			<div class="promo-icon-container">
				<div class="promo-icon-card card">
					<GlobeSVG />
					<p>Raise globally</p>
				</div>
				<div class="promo-icon-card card">
					<ChainsSVG />
					<p>Raise without censorship</p>
				</div>
			</div>
		</div>
	</section>
	<section
		class={`promo-section ${donationPromoVisible ? 'fade-in' : 'fade-out'}`}
		bind:this={donationContainer}
	>
		<div class="promo-container">
			<div class="promo-card card">
				<h2>Donate to initiatives around the world</h2>
				<p>
					Donate to unique initiatives around the globe and aid different communities and people to
					help them achieve their goals.
				</p>
				<p>
					Being built on top of blockchain technology donations are pseudo-anonymous by default. So
					you can donate to different causes with piece of mind that your identity is not
					broadcasted every time you make a donation.
				</p>
				<p>Get started donating today.</p>
				<button class="shadow-btn" on:click={() => goto('/fund-someone')}>Fund someone</button>
			</div>
			<div class="promo-icon-container">
				<div class="promo-icon-card card">
					<AidSVG />
					<p>Aid communities across the world</p>
				</div>
				<div class="promo-icon-card card">
					<AnonymousSVG />
					<p>Pseudo-anonymous donations by default</p>
				</div>
			</div>
		</div>
	</section>
</div>

<style scoped lang="scss">
	#landing-section {
		align-items: center;
		display: flex;
		flex-direction: column;
		height: 80vh;
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
			margin-bottom: 0;
			margin-top: 1rem;
		}
	}

	.promo-section {
		min-height: max-content;
		opacity: 0;
		padding-block: 5rem;
		position: relative;
	}

	.card {
		background-color: var(--surface-2);
		border-radius: 20px;
		border-top: 4px solid var(--accent);
		box-shadow:
			0 2px 2px var(--shadow-1),
			0 4px 4px var(--shadow-2);
		padding: 2rem;
	}

	.promo-container {
		display: flex;
		gap: 2.5rem;

		.promo-card {
			flex: 1;

			button {
				margin: 1rem 0;
			}
		}

		.promo-icon-container {
			display: flex;
			flex-direction: column;
			gap: 1rem;

			.promo-icon-card {
				align-items: center;
				display: flex;
				flex-direction: column;
				flex: 1;
				height: auto;
				justify-content: center;
				padding: 1rem;

				p {
					font-weight: 500;
					margin-bottom: 0;
					max-width: 155px;
					text-align: center;
				}

				img {
					border-radius: 50%;
					max-height: 100px;
					max-width: 100px;
				}
			}
		}
	}
</style>
