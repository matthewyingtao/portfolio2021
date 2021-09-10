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
	<p>{project.description}</p>
</article>
