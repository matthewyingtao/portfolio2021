<script>
	export let segment;

	import AnimatedLogo from './AnimatedLogo.svelte';

	const routes = [
		{ href: '/', name: 'Home' },
		{ href: '/projects', name: 'Projects' },
		{ href: '/contact', name: 'Contact' }
	];
</script>

<header>
	<a class="logo" href="/" aria-label="Home">
		<AnimatedLogo />
	</a>

	<nav>
		{#each routes as route}
			<div
				class="nav-item"
				class:current={route.href === segment}
				class:inactive={route.href != segment}
			>
				<a href={route.href}>{route.name}</a>
				<svg preserveAspectRatio="none" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 75 13">
					<path
						class="link-underline"
						pathLength="1"
						d="M0 13c1-9 8 3 5-6-.71-2.12 5.85 3.64 7.5 2.5 4-1.88 7.73-3.85 20.5-5.5 11.17-1.45 37.5 4 42-4"
						fill="none"
					/>
				</svg>
			</div>
		{/each}
	</nav>
</header>

<style>
	header {
		width: 100%;
		display: flex;
		flex-wrap: wrap;
		justify-content: space-between;
		align-items: flex-start;
		padding: 2rem 2rem 0 2rem;
	}

	.logo {
		margin-bottom: 2rem;
	}

	nav {
		display: grid;
		grid-template-columns: repeat(3, max-content);
		grid-gap: 1.5rem;
	}

	.nav-item {
		position: relative;
		width: max-content;
	}

	nav a {
		font-family: 'caveat', cursive;
		font-size: 2rem;
		color: #fff;
		text-decoration: none;
		transition: color 350ms ease-out;
	}

	.nav-item svg {
		position: absolute;
		bottom: -1rem;
		left: -0.5rem;
		right: -0.5rem;
		width: calc(100% + 1rem);
		height: 1rem;
		overflow: visible;
		transition: transform 350ms ease-in-out;
		pointer-events: none;
	}

	.link-underline {
		stroke-dasharray: 1;
		stroke-dashoffset: 1;
		stroke: none;
		stroke-linecap: round;
		stroke-width: 2px;
		transition: stroke-dashoffset 500ms ease-in-out;
	}

	.inactive.nav-item:hover .link-underline {
		animation: dash 500ms ease-out forwards;
	}

	.current svg {
		transform: translateY(-0.25rem);
	}

	.current a {
		color: var(--blue-700);
	}

	.current .link-underline {
		stroke-dashoffset: 0;
		stroke: #e06666;
	}

	@keyframes dash {
		0% {
			stroke-dashoffset: 1;
			stroke: none;
		}
		1% {
			stroke-dashoffset: 0.98;
			stroke: #e06666;
		}
		100% {
			stroke-dashoffset: 0;
			stroke: #e06666;
		}
	}
</style>
