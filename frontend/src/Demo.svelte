<script lang="ts">
	import World from "./World.svelte";
</script>

<div id="parent">
	<div id="paper">
		<World />
	</div>
</div>

<style lang="sass">
	#parent
		padding: 1em
		background-color: var(--palette-dark-purple)

	#paper
		border-top-right-radius: 2em
		background-color: var(--palette-white)
</style>
