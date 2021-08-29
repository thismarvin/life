<script lang="ts">
	import About from "./About.svelte";
	import Demo from "./Demo.svelte";
	import Divider from "./Divider.svelte";
</script>

<main id="parent">
	<div id="container">
		<div id="left" class="centered">
			<Demo />
		</div>
		<div id="right" class="centered">
			<About />
			<Divider />
		</div>
	</div>
</main>

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
	
	#parent
		width: 100%
		height: 100%
		background-color: var(--palette-white)

		@include large
			display: flex
			justify-content: center
			align-items: center

			background-color: var(--palette-light-gray)

	#container
		@include large
			display: grid
			grid-template-columns: 1fr 1fr
			grid-template-rows: 1fr

			margin: 1.5em
			border-top-right-radius: 1.5em
			border-bottom-left-radius: 1.5em
			box-shadow: 0.5em 0.5em 1em rgba(0, 0, 0, 0.25)

		@include full
			grid-template-columns: 1.2fr 0.8fr

	#left
		padding: 1em
		background-color: var(--palette-dark-purple)

		@include medium
			padding: 2em 0

		@include large
			border-bottom-left-radius: 1.5em
			padding: 0

	#right
		flex-direction: column
		background-color: var(--palette-white)
		
		@include large
			border-top-right-radius: 1.5em
</style>
