<script lang="ts">
	import World from "./World.svelte";
</script>

<div id="parent" class="centered">
	<div id="paper">
		<World />
	</div>
</div>

<style lang="sass">
	#parent
		background-color: var(--palette-white)

	#parent
		padding: 2em 0 1.5em 0
		background-color: #0f004e

	#paper
		padding: 4.5em 1em 0em 1em
		background-color: var(--palette-white)
		border-top-right-radius: 2em
</style>
