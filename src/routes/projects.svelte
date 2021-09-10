<script>
	import * as projects from '../data/projects.json';
	console.log(projects);
</script>

<div id="projects">
	{#each projects.projects as project}
		<div class="project">
			<div class="project-description">
				<h3>{project.name}</h3>
				<p>
					{project.description}
				</p>
			</div>
			<div class="project-img-wrapper">
				<img class="project-img" src="/projects/{project.img}" alt="" />
				<div class="project-img-bg" />
			</div>
		</div>
	{/each}
</div>

<style>
	#projects {
		max-width: 1440px;
		margin: 6rem auto;
		display: grid;
		gap: 2rem;
		transform-style: preserve-3d;
	}
	.project {
		display: flex;
		flex-direction: column;
	}

	.project-img-wrapper {
		isolation: isolate;
		position: relative;
		perspective-origin: 50% 50%;
		perspective: 50rem;
	}

	.project-img {
		display: block;
		width: 100%;
		transform: rotateY(-10deg);
	}

	.project-img-bg {
		display: block;
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		z-index: -1;
		background-color: var(--red-500);
		transform: rotate(2deg) rotateY(-10deg);
	}

	@media screen and (min-width: 600px) {
		.project {
			flex-direction: row;
			justify-content: space-between;
		}
		.project-img-wrapper {
			width: clamp(225px, 50%, 608px);
		}
		.project-description {
			width: 50%;
		}
	}
</style>
