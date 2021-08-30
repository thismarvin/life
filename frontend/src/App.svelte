<script lang="ts">
	import About from "./About.svelte";
	import Demo from "./Demo.svelte";
	import Divider from "./Divider.svelte";
</script>

<main id="parent">
	<div id="wrapper">
		<div id="container">
			<div id="left" class="centered">
				<Demo />
			</div>
			<div id="right" class="centered">
				<About />
				<Divider />
			</div>
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
		@include large
			display: flex
			height: 100%

	#wrapper
		@include large
			margin: auto
			padding: 1rem

	#container
		@include large
			display: grid
			grid-template-columns: 1fr 1fr
			grid-template-rows: 1fr

			border-top-right-radius: 1.5rem
			border-bottom-left-radius: 1.5rem
			box-shadow: 0.5rem 0.5rem 1rem rgba(0, 0, 0, 0.25)

		@include full
			grid-template-columns: 1.2fr 0.8fr

	#left
		padding: 1rem
		background-color: var(--palette-dark-purple)

		@include medium
			padding: 2rem 0

		@include large
			border-bottom-left-radius: 1.5rem
			padding: 0

	#right
		flex-direction: column
		background-color: var(--palette-white)
		
		@include large
			border-top-right-radius: 1.5rem
</style>
