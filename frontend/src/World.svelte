<script lang="ts">
	import { onMount } from "svelte";

	enum CellType {
		None = 0,
		Dead = 1,
		Alive = 2,
	}

	function cellTypeToString(type: CellType): string {
		switch (type) {
			case CellType.Dead:
				return "dead";
			case CellType.Alive:
				return "alive";
			default:
				return "";
		}
	}

	function cellTypeOpposite(type: CellType): CellType {
		switch (type) {
			case CellType.Dead:
				return CellType.Alive;
			case CellType.Alive:
				return CellType.Dead;
			default:
				CellType.None;
		}
	}

	export let width = 15;
	export let height = 15;
	export let data: CellType[][] = [];

	let paused = false;

	for (let i = 0; i < height; ++i) {
		data.push(new Array(width).fill(CellType.Dead));
	}

	randomize();

	function togglePlay() {
		paused = !paused;
	}

	function get(x: number, y: number): CellType {
		if (x < 0 || x >= width || y < 0 || y >= height) {
			return CellType.None;
		}

		return data[y][x];
	}

	function set(x: number, y: number, value: CellType) {
		data[y][x] = value;
	}

	function randomize() {
		for (let y = 0; y < height; ++y) {
			for (let x = 0; x < width; ++x) {
				data[y][x] = Math.random() > 0.6 ? CellType.Alive : CellType.Dead;
			}
		}
	}

	function clear() {
		for (let y = 0; y < height; ++y) {
			for (let x = 0; x < width; ++x) {
				data[y][x] = CellType.Dead;
			}
		}
	}

	function getTotalNeighbors(x: number, y: number): number {
		let total = 0;

		total = get(x - 1, y - 1) === CellType.Alive ? total + 1 : total;
		total = get(x + 0, y - 1) === CellType.Alive ? total + 1 : total;
		total = get(x + 1, y - 1) === CellType.Alive ? total + 1 : total;
		total = get(x + 1, y + 0) === CellType.Alive ? total + 1 : total;
		total = get(x + 1, y + 1) === CellType.Alive ? total + 1 : total;
		total = get(x + 0, y + 1) === CellType.Alive ? total + 1 : total;
		total = get(x - 1, y + 1) === CellType.Alive ? total + 1 : total;
		total = get(x - 1, y + 0) === CellType.Alive ? total + 1 : total;

		return total;
	}

	function update(deltaTime: number) {
		if (paused) {
			return;
		}

		let temp = [];

		for (let y = 0; y < height; ++y) {
			temp.push(new Array());

			for (let x = 0; x < width; ++x) {
				const current = get(x, y);
				const neighbors = getTotalNeighbors(x, y);

				if (current === CellType.Alive) {
					if (neighbors < 2 || neighbors > 3) {
						temp[y].push(CellType.Dead);
						continue;
					}
				}

				if (current === CellType.Dead) {
					if (neighbors === 3) {
						temp[y].push(CellType.Alive);
						continue;
					}
				}

				temp[y].push(current);
			}
		}

		for (let y = 0; y < height; ++y) {
			for (let x = 0; x < width; ++x) {
				data[y][x] = temp[y][x];
			}
		}
	}

	const target = 0.5;

	let totalElapsedTime = 0;
	let accumulator = 0;

	function loop(timeStamp: number) {
		let deltaTime = (timeStamp - totalElapsedTime) / 1000;

		if (Number.isNaN(deltaTime)) {
			deltaTime = 0;
		}

		totalElapsedTime = timeStamp;

		accumulator += deltaTime;

		while (accumulator >= target) {
			update(target);

			accumulator -= target;
		}

		requestAnimationFrame((timeStamp) => loop(timeStamp));
	}

	onMount(() => loop(0));
</script>

<div
	id="parent"
	style="--size: calc((100vw - 2em - 3em - 2px * {width} - 4px) / {width});"
>
	<div id="grid">
		{#each data as row, y}
			<div class="row">
				{#each row as cell, x}
					<div
						class="centered cell"
						on:click={() => set(x, y, cellTypeOpposite(cell))}
					>
						<div class={`inner-cell ${cellTypeToString(cell)}`} />
					</div>
				{/each}
			</div>
		{/each}
	</div>
	<div id="controlPanel">
		<div>
			<button on:click={randomize}>Randomize</button>
			<button on:click={clear}>Clear</button>
		</div>
		<div>
			<button id="pause" on:click={togglePlay}
				>{paused ? "Resume" : "Pause"}</button
			>
		</div>
	</div>
</div>

<style lang="sass">
	button
		border: 2px solid var(--palette-black)
		padding: 0.9em 1.2em
		background-color: var(--palette-light-gray)

	#parent
		padding: 4em 1.5em 1.5em 1.5em

	#grid
		border: 2px solid var(--palette-black)

	#controlPanel
		display: flex
		justify-content: space-between

		padding-top: 1.5em	

	#pause
		width: 86px

	.row
		display: flex

	.cell
		margin: 0
		border-right: 2px solid var(--palette-light-gray)
		border-bottom: 2px solid var(--palette-light-gray)
		padding: 0
		width: var(--size)
		height: var(--size)
		background-color: var(--palette-white)
		
	.inner-cell
		width: 0
		height: 0
		transition: all 0.3s ease-in

	.alive
		width: var(--size)
		height: var(--size)
		background-color: var(--palette-black)
</style>
