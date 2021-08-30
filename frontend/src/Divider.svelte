<script lang="ts">
	import DisplayWorld from "./DisplayWorld.svelte";

	export let width = 10;
	export let height = 10;
</script>

<div id="parent">
	<DisplayWorld {width} {height} wrap={true} autoReset={true} />
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
		margin: auto
		padding-bottom: 1rem

		@include medium
			padding-bottom: 2rem

		@include full
			padding-bottom: 2.5rem
</style>
