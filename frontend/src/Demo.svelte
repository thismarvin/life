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
		@media (min-width: 580px)
			@content	

	@mixin large
		@media (min-width: 900px)
			@content
		
	@mixin full
		@media (min-width: 1200px)
			@content

	#parent
		max-width: calc(1.5rem + 2px + 32px * 15 + 2px + 1.5rem)

		@include large
			padding: 2rem
		
		@include full
			padding: 6rem 0

	#paper
		border-top-right-radius: 2rem
		background-color: var(--palette-white)
</style>
