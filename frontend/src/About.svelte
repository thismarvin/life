<script lang="ts">
</script>

<div id="parent">
	<div id="info">
		<hr />
		<h2>Conway's Game of Life</h2>
		<p>
			a cellular automaton that mimics life by following a set of four simple
			rules
		</p>
		<h4>Learn More</h4>
		<ul>
			<li>
				<a
					class="link"
					href="https://en.wikipedia.org/wiki/Conway%27s_Game_of_Life"
					>Wikipedia Article</a
				>
			</li>
			<li>
				<a class="link" href="https://youtu.be/R9Plq-D1gEk"
					>Computerphile YouTube Video</a
				>
			</li>
		</ul>
	</div>
</div>

<style lang="sass">
	@mixin medium
		@media (min-width: 580px)
			@content	

	@mixin large
		@media (min-width: 900px)
			@content
		
	@mixin full
		@media (min-width: 1200px)
			@content

	*
		color: var(--palette-white)

	hr
		border: 0
		height: 0.5em
		background: linear-gradient(90deg, var(--palette-red), var(--palette-purple))

	p
		color: var(--palette-light-gray)

	#parent
		padding: 1em
		max-width: 528px

		@include medium
			padding: 2em

		@include full
			padding-top: 6em

	#info
		border-bottom-left-radius: 2em
		padding: 2em 1em
		background-color: var(--palette-dark-purple)
</style>
