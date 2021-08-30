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
		@media (min-width: 680px)
			@content	

	@mixin large
		@media (min-width: 1024px)
			@content
		
	@mixin full
		@media (min-width: 1200px)
			@content

	*
		color: var(--palette-white)

	hr
		border: 0
		height: 0.5rem
		background: linear-gradient(90deg, var(--palette-red), var(--palette-purple))

	p
		color: var(--palette-light-gray)

	#parent
		padding: 1rem
		max-width: 528px

		@include medium
			padding: 2rem

		@include full
			padding: 2.5rem

	#info
		border-bottom-left-radius: 2rem
		padding: 2rem 1rem
		background-color: var(--palette-dark-purple)
</style>
