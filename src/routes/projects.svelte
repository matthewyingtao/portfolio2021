<script>
	import * as projects from '../data/projects.json';
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
			<div class="scene">
				<a class="project-img-wrapper" href="/">
					<div class="project-img-overlay">
						<p>click to see more</p>
					</div>
					<img class="project-img" src="/projects/{project.img}" alt="" />
				</a>
			</div>
		</div>
	{/each}
</div>

<style>
	#projects {
		max-width: 1440px;
		margin: 6rem auto;
		display: grid;
		gap: 5rem;
	}

	.project {
		display: flex;
		flex-direction: column;
		margin-right: 2rem;
	}

	.project-description {
		max-width: 55ch;
	}

	.project-description h3 {
		font-size: 2.5rem;
		font-weight: bold;
		margin-bottom: 1rem;
	}

	.scene {
		position: relative;
		perspective: 50rem;
		perspective-origin: 100% 100%;
		transform-style: preserve-3d;
	}

	.project-img-wrapper {
		display: block;
		transform: rotateX(7deg) rotateY(-10deg);
		transition: transform 350ms ease;
	}

	.project-img-wrapper:hover {
		transform: rotateX(0deg) rotateY(0deg);
	}

	.project-img-overlay {
		display: flex;
		justify-content: center;
		align-items: center;
		position: absolute;
		z-index: 1;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background: rgba(0, 0, 0, 0.5);
		opacity: 0;
		transition: opacity 350ms ease;
	}

	.project-img-overlay p {
		font-size: 2.5rem;
		color: white;
	}

	.project-img-wrapper:hover .project-img-overlay {
		opacity: 1;
	}

	.project-img {
		display: block;
		width: 100%;
		box-shadow: 2rem 2rem 0 -1rem var(--red-500);
		transition: box-shadow 150ms ease;
		border: 1px solid white;
	}

	.project-img-wrapper:active .project-img {
		box-shadow: 1rem 1rem 0 -1rem var(--red-500);
	}

	@media screen and (min-width: 600px) {
		.project {
			flex-direction: row;
			justify-content: center;
			align-items: center;
		}
		.scene {
			width: clamp(225px, 50%, 608px);
		}
		.project-description {
			width: 50%;
		}
	}
</style>
