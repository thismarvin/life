<script lang="ts">
	import World from "./World.svelte";
</script>

<div id="demo">
	<World />
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

	#demo
		margin: auto
		padding: 1rem
		max-width: calc(2rem + 0.5rem + 4px + 32px * 15)

		@include medium
			padding: 2rem
</style>
