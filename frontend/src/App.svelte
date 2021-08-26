<script lang="ts">
	import World from "./World.svelte";
</script>

<main>
	<section id="head">
		<h4>/home/marvin/demos/life</h4>
	</section>

	<section id="demo">
		<World />
	</section>

	<div id="info">
		<section id="header">
			<div class="entry">
				<h4>TypeScript + Svelte</h4>
				<hr class="gradient" />
				<h3>Conway's</h3>
				<h1>Game of Life</h1>
			</div>
		</section>

		<section id="description">
			<div>
				<p>
					Lorem ipsum dolor sit, amet consectetur adipisicing elit. Distinctio
					voluptas pariatur facere natus nostrum necessitatibus nemo eaque
					soluta temporibus odio dolor, enim expedita eveniet voluptatibus
					corrupti quisquam dicta quibusdam commodi.
				</p>
				<ul>
					<li>
						Lorem ipsum dolor sit amet consectetur adipisicing elit. Optio
						ipsam.
					</li>
					<li>
						Lorem ipsum dolor sit amet consectetur adipisicing elit. Dignissimos
						itaque atque natus.
					</li>
					<li>Lorem ipsum dolor sit amet consectetur.</li>
				</ul>
				<p>
					Lorem ipsum dolor, sit amet consectetur adipisicing elit. Sunt sit
					debitis ad nemo rem ea, dignissimos id, fugit eius voluptatem,
					laudantium eaque natus quisquam placeat. Eius fugiat corporis facilis
					excepturi.
				</p>
				<h4>Reference</h4>
				<ul>
					<li>
						<a
							class="lin"
							href="https://en.wikipedia.org/wiki/Conway%27s_Game_of_Life"
							>Wikipedia Article</a
						>
					</li>
					<li>
						<a class="lin" href="https://youtu.be/R9Plq-D1gEk"
							>Computerphile YouTube Video</a
						>
					</li>
				</ul>
			</div>
			<div id="footer">
				<a class="link" href="https://github.com/thismarvin/life"
					>View Source Code</a
				>
			</div>
		</section>
	</div>
</main>

<style lang="sass">
	:root
		--width: 8
		--height: 8
		--size: 16px

	// main
	// 	margin: 0 0.8em
	
	h1, h3, h4
		margin: 0

	h1
		font-size: 2em
		text

	h3
		font-size: 1.2em

	h4
		font-size: 0.9em
		opacity: 0.9

	hr
		height: 0.2em
		border: 0
		background: black
		margin-bottom: 1.2em
	
	.gradient
		height: 0.5em
		background: linear-gradient(90deg, #ff004d, #b200ff)

	p
		font-size: 1.1em
		opacity: 0.9

	ul
		padding-left: 2em

	.entry
		margin-bottom: 2em

	#head
		margin: 2em 2em 0 2em
		mar

	#info
		background: #0f004e
		margin-top: 4em
		padding: 3em 2em
		color: white
		//border-top-left-radius: 2em
		//border-top-right-radius: 3em

	#demo
		display: flex
		align-content: center
		justify-content: center
		margin-top: 4em
		margin-bottom: 4em

	#footer
		margin-top: 2em
		display: flex

	ul
		margin-bottom: 1.5em
	
	li
		margin-bottom: 0.5em

	.link
		margin: 1em 0.3em 
		padding: 0.5em 1em
		border: 2px solid white
		background: transparent
		width: 100%
		text-align: center
		//border-radius: 3em
		font-size: 1.3em
		text-decoration: none
		color: white

	.lin
		color: #ff004d
		text-decoration: none

</style>
