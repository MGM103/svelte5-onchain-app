<script>
</script>

<nav>
	<h2><a id="nav-logo" href="/">Go Fund Yourself</a></h2>
	<ul id="links-container">
		<li><a href="/fund-yourself">Fund yourself</a></li>
		<li><a href="/fund-someone">Fund someone</a></li>
		<button>Connect</button>
	</ul>
</nav>

<style scoped lang="scss">
	nav {
		align-items: center;
		display: flex;
		flex-direction: row;
		gap: 2.5rem;
		margin-inline: auto;
		position: sticky;
		top: 0;
		width: 100%;
		z-index: 1;

		#nav-logo {
			display: block;
			position: relative;
			width: max-content;
		}

		ul {
			align-items: center;
			display: flex;
			gap: 2rem;
			position: relative;
			width: 100%;
		}

		a {
			color: var(--secondary);
			text-decoration: none;

			&:hover:not(#nav-logo) {
				transform: scale(1.025);
				transition: transform 0.1s ease;
			}
		}

		button {
			background-color: var(--tertiary);
			border-radius: 6px;
			border: none;
			color: var(--surface-1);
			cursor: pointer;
			font-weight: 550;
			margin-left: auto;
			padding: 10px 12px;
			width: 100px;
		}

		// #mobile-menu-btn {
		// 	background-color: transparent;
		// 	border: none;
		// 	display: none;
		// 	z-index: 1;
		// }

		&::before {
			content: '';
			background-color: var(--surface-1);
			// box-shadow: var(--nav-shadow);
			height: 100%;
			top: 0;
			left: 50%;
			position: absolute;
			transform: translateX(-50%);
			transition: box-shadow 0.5s ease;
			width: 100vw;
			z-index: 0;
		}
	}
</style>
