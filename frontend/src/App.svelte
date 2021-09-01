<script lang="ts">
	import About from "./About.svelte";
	import Demo from "./Demo.svelte";
	import Footer from "./Footer.svelte";
	import Nav from "./Nav.svelte";
</script>

<main id="app">
	<div id="nav-wrapper">
		<Nav />
	</div>
	<section id="container">
		<div id="demo-wrapper">
			<Demo />
		</div>
		<div id="about-wrapper">
			<About />
		</div>
	</section>
	<Footer />
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

	#app
		height: 100%	

	#container
		display: flex
		flex-direction: column

	#nav-wrapper
		padding-top: 2rem

	#demo-wrapper
		display: flex
		background-color: var(--palette-dark-purple)

		@include full
			height: calc(4rem + 0.5rem + 2rem + 4px + 32px * 15 + 1.5rem + 2rem + 63px)

	#about-wrapper
		display: flex
		background-color: var(--palette-white)
</style>
