<script lang="ts">
</script>

<div id="about">
	<div id="info">
		<h2>Conway's Game of Life</h2>
		<hr />
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
					>Numberphile YouTube Video</a
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
		height: 0.25rem
		background: linear-gradient(90deg, var(--palette-red), var(--palette-purple))

	h2
		font-weight: bold
		margin-bottom: 0.75rem

	h4
		margin: 1rem 0

	p
		color: var(--palette-light-gray)

	ul
		padding-left: 2rem

	#about
		margin: auto
		padding: 1rem
		max-width: 450px
		background-color: var(--palette-white)

		@include medium
			padding: 2rem

	#info
		padding: 1.5rem
		border-radius: 1rem
		box-shadow: 0.5rem 0.5rem 1rem rgba(0, 0, 0, 0.25)
		background-color: var(--palette-dark-purple)

		@include medium
			padding: 2rem
</style>
