<script>
	import { onMount } from 'svelte';
	import AOS from 'aos';
	import 'aos/dist/aos.css';

	onMount(() => {
		AOS.init({
			duration: 500,
			easing: 'ease-out',
			once: true,
			disable: 'mobile'
		});
	});
</script>

<div class="intro">
	<img data-aos="fade-up" src="/blobPortrait.webp" alt="blob" />
	<div data-aos="fade-up" data-aos-delay="150" class="welcome-text">
		<h1>Hello there!</h1>
		<p>I'm Matthew Tao, an Auckland-based web developer.</p>
	</div>
</div>

<style>
	.intro {
		display: flex;
		flex-direction: column-reverse;
		justify-content: left;
		align-items: center;
	}
	.intro img {
		display: block;
		width: 100%;
		max-width: 608px;
		margin: 0 8rem;
	}

	.welcome-text {
		max-width: 45rem;
		margin-bottom: 2rem;
	}

	.welcome-text h1 {
		font-size: 4rem;
		font-weight: bold;
	}

	.welcome-text p {
		font-size: 2.5rem;
	}
	@media (min-width: 800px) {
		.intro {
			flex-direction: row;
		}
		.intro img {
			width: clamp(225px, 35%, 608px);
			margin: 0 6rem 0 10%;
		}
		.welcome-text {
			margin: 0rem;
		}
	}

	@media (min-width: 1200px) {
		.welcome-text h1 {
			font-size: 5.5rem;
			font-weight: bold;
		}
		.welcome-text p {
			font-size: 4rem;
		}
	}
</style>
