<script>
	import PageTransition from '../../components/PageTransition.svelte';
	import projects from '../../data/projects.json';

	let showPersonal = true;
</script>

<div id="projects">
	<div class="heading">
		<h1>Projects</h1>
		<div class="chip-container">
			<button class:active={showPersonal} class="chip" on:click={() => (showPersonal = true)}>
				Personal
			</button>
			<button class:active={!showPersonal} class="chip" on:click={() => (showPersonal = false)}>
				Collaborative
			</button>
		</div>
	</div>

	<PageTransition refresh={showPersonal}>
		{#if showPersonal}
			{#each projects.personal as project}
				<article class="project">
					<div class="project-description">
						<h3>{project.friendlyName}</h3>
						<p>{project.description}</p>
					</div>
					<a
						class="project-img-wrapper"
						href="/projects/{project.name}"
						aria-label="read more about {project.friendlyName}."
					>
						<div class="project-img-overlay"><p>Go to project</p></div>
						<img class="project-img" src="/projects/{project.img}" alt="" />
						<div class="project-img-shadow" />
					</a>
				</article>
			{/each}
		{:else}
			{#each projects.collaborative as project}
				<article class="project">
					<div class="project-description">
						<h3>{project.friendlyName}</h3>
						<p>
							{project.description}
						</p>
					</div>
					<a
						class="project-img-wrapper"
						href={project.link}
						aria-label="go to the website."
						target="_blank"
						rel="noopener noreferrer"
					>
						<div class="project-img-overlay"><p>View Website</p></div>
						<img class="project-img" src="/projects/{project.img}" alt="" />
						<div class="project-img-shadow" />
					</a>
				</article>
			{/each}
		{/if}
	</PageTransition>
</div>

<style>
	#projects {
		max-width: 1140px;
		margin: 2rem auto 6rem auto;
		gap: 5rem;
	}

	h1 {
		font-family: 'Raleway', sans-serif;
		font-weight: bold;
		margin-bottom: 1rem;
	}

	.heading {
		display: flex;
		justify-content: space-between;
		align-items: center;
		flex-wrap: wrap;
		margin-bottom: 1rem;
	}

	.chip-container {
		display: grid;
		grid-template-columns: repeat(2, max-content);
		gap: 1rem;
		margin-bottom: 1rem;
	}

	.chip {
		position: relative;
		background: transparent;
		border: 2px solid #fff;
		color: #fff;
		padding: 0.5rem 1rem;
		border-radius: 999px;
		overflow: hidden;
	}

	.chip:before,
	.chip:after {
		content: '';
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		opacity: 0;
		transition: opacity 350ms ease-out;
	}

	.chip::before {
		z-index: -2;
		background: linear-gradient(to right, var(--blue-500), var(--blue-600));
	}

	.chip::after {
		z-index: -1;
		background: linear-gradient(to right, var(--red-500), var(--red-600));
	}

	.chip:hover::before {
		opacity: 1;
	}

	.chip.active::after {
		opacity: 1;
	}

	.project {
		display: flex;
		flex-direction: column;
		margin-bottom: 6rem;
	}

	.project-description {
		--border-style: 2px solid var(--blue-500);
		position: relative;
		max-width: 55ch;
		margin-bottom: 2rem;
	}

	/* border left and bottom of div */
	.project-description::before {
		content: '';
		position: absolute;
		top: 0;
		left: 0;
		bottom: 0;
		width: 3rem;
		border-left: var(--border-style);
		border-bottom: var(--border-style);
		border-bottom-left-radius: 1rem;
	}

	/* border top */
	.project-description h3 {
		border-top: var(--border-style);
		font-size: 2.5rem;
		font-weight: bold;
		margin-bottom: 0.5rem;
		width: max-content;
		position: relative;
		padding: 0.5rem 1rem 0.5rem 1.5rem;
	}

	/* border top, right and bottom of heading */
	.project-description h3::after {
		content: '';
		position: absolute;
		top: -2px;
		width: 1rem;
		margin-left: 1rem;
		height: 100%;
		border-top: var(--border-style);
		border-right: var(--border-style);
		border-bottom: var(--border-style);
		border-top-right-radius: 999px;
	}

	.project-description p {
		padding-left: 1.5rem;
		padding-bottom: 0.5rem;
	}

	.project-img-wrapper {
		--border-radius: 0.5rem;
		position: relative;
		perspective: 50rem;
		outline: 1px solid transparent;
		transform-style: preserve-3d;
		margin-right: 1rem;
		isolation: isolate;
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
		background: linear-gradient(
			to bottom,
			rgba(var(--slate-400-rgb), 0.5),
			rgba(var(--blue-500-rgb), 0.7)
		);
		opacity: 0;
		transition: opacity 350ms ease;
		border: 2px solid white;
		border-radius: var(--border-radius);
	}

	.project-img-overlay p {
		font-size: 2.5rem;
		letter-spacing: 3px;
		text-transform: uppercase;
		color: white;
		border-bottom: 2px solid white;
	}

	.project-img-wrapper:hover .project-img-overlay {
		opacity: 1;
	}

	.project-img {
		position: relative;
		display: block;
		width: 100%;
		transition: box-shadow 150ms ease;
		border: 2px solid white;
		border-radius: var(--border-radius);
	}

	.project-img-shadow {
		position: absolute;
		display: block;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		z-index: -1;
		border-radius: var(--border-radius);
		background: linear-gradient(
			to bottom,
			rgba(var(--blue-600-rgb), 0),
			rgba(var(--blue-500-rgb), 0.4)
		);
		transform: translate(1rem, 1rem);
		transition: transform 150ms ease-out;
	}

	.project-img-wrapper:active .project-img-shadow {
		transform: translate(0, 0);
	}

	@media screen and (min-width: 800px) {
		.project {
			flex-direction: row;
			justify-content: center;
			align-items: center;
			min-height: 70vh;
		}
		.project:nth-of-type(2n) {
			flex-direction: row-reverse;
		}
		.project:nth-of-type(2n) .project-img-wrapper {
			transform: perspective(40rem) rotateX(7deg) rotateY(10deg);
		}
		.project-img-wrapper {
			display: block;
			transform: perspective(40rem) rotateX(7deg) rotateY(-10deg);
			transition: transform 350ms ease;
			width: clamp(225px, 50%, 608px);
			margin-left: 2rem;
			margin-right: 3rem;
		}

		.project:nth-of-type(2n) .project-img-wrapper {
			margin-right: 2rem;
			margin-left: 4rem;
		}

		.project-description {
			width: 50%;
		}

		.project-img-wrapper.project-img-wrapper:hover {
			transform: perspective(40rem) rotateX(7deg) rotateY(0deg);
		}

		.project:nth-of-type(2n) .project-img-shadow {
			transform: translate(-1rem, 1rem);
		}

		.project:nth-of-type(2n) .project-img-wrapper:active .project-img-shadow {
			transform: translate(0rem, 0rem);
		}
	}
</style>
