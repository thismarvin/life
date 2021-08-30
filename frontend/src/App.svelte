<script lang="ts">
	import About from "./About.svelte";
	import Demo from "./Demo.svelte";
	import Divider from "./Divider.svelte";
</script>

<main id="parent">
	<div id="wrapper">
		<div id="container">
			<div id="left-wrapper">
				<div id="left">
					<Demo />
				</div>
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
		@media (min-width: 680px)
			@content	

	@mixin large
		@media (min-width: 1024px)
			@content
		
	@mixin full
		@media (min-width: 1200px)
			@content
	
	#parent
		@include large
			display: flex
			height: 100%

	#wrapper
		@include medium
			margin: auto
			padding: 3rem 0 0 0

		@include large
			padding: 1rem
			
	#container
		@include medium
			margin: auto
			max-width: calc(480px + 4em + 4em)
			box-shadow: 0.5rem 0.5rem 1rem rgba(0, 0, 0, 0.25), -0.5rem 0.5rem 1rem rgba(0, 0, 0, 0.25)

		@include large
			display: grid
			grid-template-columns: 1fr 1fr
			grid-template-rows: 1fr

			max-width: 100%
			border-top-right-radius: 1.5rem
			border-bottom-left-radius: 1.5rem
			box-shadow: 0.5rem 0.5rem 1rem rgba(0, 0, 0, 0.25)

		@include full
			grid-template-columns: 1.2fr 0.8fr

	#left-wrapper
		display: flex
		background-color: var(--palette-dark-purple)

		@include large
			border-bottom-left-radius: 1.5rem

	#left
		margin: auto

		@include large
			border-bottom-left-radius: 1.5rem

	#right
		flex-direction: column
		background-color: var(--palette-white)
		
		@include large
			border-top-right-radius: 1.5rem
</style>
