<footer id="site-footer">
	<section id="top-row">
		<h2 class="h3">Go Fund Yourself</h2>
	</section>
	<section id="bottom-row">
		<div id="funding-option">
			<h3 class="h6">Funding options</h3>
			<ul>
				<li><a href="/fund-yourself">Start you own fund raise</a></li>
				<li><a href="/fund-someone">Support another cause</a></li>
			</ul>
		</div>
		<div id="about-creator">
			<ul>
				<li>0xNelli &copy {new Date().getFullYear()}</li>
			</ul>
		</div>
	</section>
</footer>

<style scoped lang="scss">
	#site-footer {
		color: var(--surface-1);
		display: flex;
		flex-direction: column;
		padding-top: 2.5rem;
		padding-bottom: 2.5rem;
		position: relative;

		#bottom-row {
			display: flex;
			flex-direction: row;
			gap: 4rem;

			#about-creator {
				align-content: end;
			}
		}

		li {
			margin-bottom: 0.25rem;
		}

		a {
			color: var(--surface-1);
			text-decoration: none;

			&:hover {
				color: var(--tertiary);
			}
		}

		&::before {
			content: '';
			background-color: var(--secondary);
			height: 100%;
			left: 50%;
			position: absolute;
			top: 0;
			transform: translateX(-50%);
			width: 100vw;
			z-index: -1;
		}
	}
</style>
