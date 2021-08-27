<script lang="ts">
	import DisplayWorld from "./DisplayWorld.svelte";

	export let width = 10;
	export let height = 10;
</script>

<div id="parent">
	<div id="divider" class="centered">
		<DisplayWorld {width} {height} wrap={true} autoReset={true} />
	</div>
</div>

<style lang="sass">

</style>
