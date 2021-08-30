<script lang="ts">
	import World from "./World.svelte";
</script>

<div id="parent">
	<div id="paper">
		<World />
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

	#parent
		padding: 1rem
		max-width: calc(1.7rem + 2px + 32px * 15 + 2px + 1.7rem)

		@include medium
			padding: 2rem	

		@include large
			padding: 0 2rem
		
		@include full
			padding: 0

	#paper
		border-top-right-radius: 2rem
		background-color: var(--palette-white)
</style>
