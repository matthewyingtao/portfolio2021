<script context="module">
	import projects from '../../data/projects.json';

	export async function load(ctx) {
		let slug = ctx.page.params.slug;
		// return the project with the name of the project in the object
		let project = projects.projects.find((project) => project.name === slug);
		return { props: { project } };
	}
</script>

<script>
	export let project;
</script>

<article>
	<h1>{project.friendlyName}</h1>
	<p class="summary">{project.description}</p>
	<img src="/projects/{project.img}" alt={project.name} />
</article>

<style>
	article {
		max-width: 65rem;
		margin: 6rem auto;
		color: white;
		border-radius: 1rem;
		padding: 1rem;
		background: linear-gradient(to bottom, var(--red-500) 0%, var(--red-600) 100%);
		background: #e06666;
		box-shadow: inset 20px 20px 60px #b55353, inset -20px -20px 60px #ff7979;
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
