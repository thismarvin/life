<script lang="ts">
	import Demo from "./Demo.svelte";
	import About from "./About.svelte";
	import Divider from "./Divider.svelte";
</script>

<main>
	<Demo />
	<About />
	<Divider height={10} />

	<!-- <div id="info">
		<section id="header">
			<div class="entry">
				<h3>Conway's</h3>
				<h1>Game of Life</h1>
				<hr class="gradient" />
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
	</div> -->
</main>

<style lang="sass">
	:root
		--width: 8
		--height: 8
		--size: 16px

		--palette-background: #0f004e
		--palette-purple: #603aff

	.centered
		display: flex
		justify-content: center
		align-items: center

	.display
		//display: grid
		//padding: 4em 0
		//grid-template-areas: "a ." "b b" "b b" ". c"

	// #display-rack
	// 	display: block

	#display-a
		//height: 80vw
		background-color: #0f004e
		//background: linear-gradient(0deg, #ff004d, #b200ff)
		//background-color: var(--palette-background)
		
	#display-b
		//height: 70vw
		background-color: #8062ff

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
		margin: 2em 1.5em 0 1.5em
		font-size: 1.1em

	#info
		background: #0f004e
		margin-top: 4em
		padding: 3em 1.5em
		color: white
		//border-top-left-radius: 2em
		//border-top-right-radius: 3em

	#demo
		padding: 4em 0

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
