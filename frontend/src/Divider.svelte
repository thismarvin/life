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
		@media (min-width: 580px)
			@content	

	@mixin large
		@media (min-width: 900px)
			@content
		
	@mixin full
		@media (min-width: 1200px)
			@content

	#parent
		margin: auto

		@include medium
			padding-bottom: 2em

		@include full
			padding-bottom: 6em
</style>
