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

	export const width = 20;
	export const height = 20;

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

<div class="container">
	<div class="grid">
		{#each data as row, y}
			<div class="row">
				{#each row as cell, x}
					<div class="cell" on:click={() => set(x, y, cellTypeOpposite(cell))}>
						<div class={`inner-cell ${cellTypeToString(cell)}`} />
					</div>
				{/each}
			</div>
		{/each}
	</div>
	<div class="controlPanel">
		<div>
			<button on:click={randomize}>Randomize</button>
			<button on:click={clear}>Clear</button>
		</div>
		<div>
			<button on:click={togglePlay}>{paused ? "Resume" : "Pause"}</button>
		</div>
	</div>
</div>

<style lang="sass">
	:root
		--size: 14px
		--black: rgb(33, 33, 33)
		--gray: rgb(230, 230, 230)

	button
		padding: 0.6em 1em
		background-color: rgb(245, 245, 245)
		border: 2px solid var(--black)

	.container
		display: block

	.grid
		border: 2px solid var(--black)	

	.row
		display: flex

	// .cell
	// 	margin: 0
	// 	padding: 0
	// 	width: var(--size)
	// 	height: var(--size)
	// 	border-right: 1px solid gray
	// 	border-bottom: 1px solid gray
	// 	transition: all 0.19s ease

	.cell
		margin: 0
		padding: 0
		width: var(--size)
		height: var(--size)
		border-right: 2px solid var(--gray)
		border-bottom: 2px solid var(--gray)
		display: flex
		justify-content: center
		align-items: center
		
	.inner-cell
		margin: 0
		padding: 0
		width: 0
		height: 0
		transition: all 0.3s ease-in

	.alive
		background-color: var(--black)
		width: calc(var(--size))
		height: calc(var(--size))

	.controlPanel
		margin: 1em 0em	
		display: flex
		justify-content: space-between

</style>
