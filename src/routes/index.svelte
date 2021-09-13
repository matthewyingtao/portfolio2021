<script>
	import { onMount } from 'svelte';
	import AOS from 'aos';
	import 'aos/dist/aos.css';

	onMount(async () => {
		AOS.init({
			duration: 600,
			easing: 'ease-out',
			disable: 'mobile',
			once: true
		});
		//wait for the page to load before initializing AOS
		await new Promise((resolve) => setTimeout(resolve, 800));
		AOS.refresh();
	});
</script>

<div class="intro">
	<img data-aos="fade-up" src="/blobPortrait.webp" alt="Matthew Tao" />
	<div data-aos="fade-up" data-aos-delay="150" class="welcome-text">
		<h1>Hello there!</h1>
		<p>I'm Matthew Tao, an Auckland-based Front-End developer.</p>
	</div>
</div>

<style>
	.intro {
		display: flex;
		flex-direction: column-reverse;
		justify-content: left;
		align-items: center;
		margin-top: 2rem;
	}
	.intro img {
		display: block;
		width: 100%;
		max-width: 608px;
	}

	.welcome-text {
		max-width: 45rem;
		margin: 2rem 0;
	}

	.welcome-text h1 {
		font-size: 4rem;
		font-weight: bold;
	}

	.welcome-text p {
		font-family: 'caveat', cursive;
		font-size: 2.5rem;
	}
	@media (min-width: 800px) {
		.intro {
			flex-direction: row;
		}
		.intro img {
			width: clamp(225px, 35%, 608px);
			margin-right: 6rem;
		}
		.welcome-text {
			margin: 0rem;
		}
	}

	@media (min-width: 1200px) {
		.intro {
			margin-left: 10%;
		}
		.welcome-text h1 {
			font-size: 5.5rem;
			font-weight: bold;
		}
		.welcome-text p {
			font-size: 4rem;
		}
	}
</style>
