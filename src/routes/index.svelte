<script>
	import { onMount } from 'svelte';
	import AOS from 'aos';
	import 'aos/dist/aos.css';

	onMount(() => {
		AOS.init({
			duration: 500,
			easing: 'ease-in-out'
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
		justify-content: left;
		align-items: center;
	}
	.intro img {
		display: block;
		width: clamp(225px, 35%, 608px);
		margin: 0 8rem;
	}

	.welcome-text {
		max-width: 45rem;
	}

	.welcome-text h1 {
		font-size: 5.5rem;
		font-weight: bold;
	}

	.welcome-text p {
		font-size: 4rem;
	}
</style>
