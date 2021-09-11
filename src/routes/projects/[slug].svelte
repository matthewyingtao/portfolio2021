<script context="module">
	import projects from '../../data/projects.json';

	export async function load(ctx) {
		let slug = ctx.page.params.slug;
		// return the project with the name of the project in the object
		let project = projects.personal.find((project) => project.name === slug);
		return { props: { project } };
	}
</script>

<script>
	export let project;
</script>

<div class="container">
	<img class="project-img" src={project.img} alt={project.name} />
	<article>
		<h1>{project.friendlyName}</h1>
		<p class="summary">{project.description}</p>
	</article>
</div>

<style>
	.container {
		margin: 6rem auto;
	}

	.project-img {
		display: block;
		max-width: 1440px;
		height: auto;
		margin: 0 auto;
	}

	article {
		max-width: 65rem;
		color: white;
		border-radius: 1rem;
		padding: 1rem;
		background: linear-gradient(to bottom, var(--red-500) 0%, var(--red-600) 100%);
		background: #e06666;
		box-shadow: inset 20px 20px 60px #b55353, inset -20px -20px 60px #ff7979;
		margin: 3rem auto;
	}

	h1 {
		/* font-family: 'Raleway', sans-serif; */
		font-size: 3.5rem;
		font-weight: bold;
		margin-bottom: 1rem;
	}

	.summary {
		font-style: italic;
	}

	img {
		display: block;
		width: 100%;
		border-radius: 0.75rem;
	}
</style>
