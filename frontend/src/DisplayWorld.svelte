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

	export let width = 10;
	export let height = 10;
	export let data: CellType[][] = [];

	export let wrap = false;
	export let randomized = true;
	export let autoReset = false;

	let iterations = 0;

	if (data.length === 0) {
		for (let i = 0; i < height; ++i) {
			data.push(new Array(width).fill(CellType.Dead));
		}
	}

	if (randomized) {
		randomize();
	}

	function get(x: number, y: number): CellType {
		if (wrap) {
			let wrappedX = x;
			let wrappedY = y;

			wrappedX = wrappedX < 0 ? width - 1 : wrappedX;
			wrappedX = wrappedX >= width ? 0 : wrappedX;
			wrappedY = wrappedY < 0 ? height - 1 : wrappedY;
			wrappedY = wrappedY >= height ? 0 : wrappedY;

			return data[wrappedY][wrappedX];
		}

		if (x < 0 || x >= width || y < 0 || y >= height) {
			return CellType.None;
		}

		return data[y][x];
	}

	function randomize() {
		iterations = 0;

		for (let y = 0; y < height; ++y) {
			for (let x = 0; x < width; ++x) {
				data[y][x] = Math.random() > 0.6 ? CellType.Alive : CellType.Dead;
			}
		}
	}

	function isEmpty(): boolean {
		for (let y = 0; y < height; ++y) {
			for (let x = 0; x < width; ++x) {
				if (data[y][x] === CellType.Alive) {
					return false;
				}
			}
		}

		return true;
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
		if (autoReset) {
			iterations += 1;

			if (iterations >= 10 || isEmpty()) {
				randomize();
			}
		}

		let temp = [];

		let changed = false;

		for (let y = 0; y < height; ++y) {
			temp.push(new Array());

			for (let x = 0; x < width; ++x) {
				const current = get(x, y);
				const neighbors = getTotalNeighbors(x, y);

				if (current === CellType.Alive) {
					if (neighbors < 2 || neighbors > 3) {
						temp[y].push(CellType.Dead);
						changed = true;
						continue;
					}
				}

				if (current === CellType.Dead) {
					if (neighbors === 3) {
						temp[y].push(CellType.Alive);
						changed = true;
						continue;
					}
				}

				temp[y].push(current);
			}
		}

		if (!changed) {
			randomize();
			return;
		}

		for (let y = 0; y < height; ++y) {
			for (let x = 0; x < width; ++x) {
				data[y][x] = temp[y][x];
			}
		}
	}

	const target = 1.5;

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

<div id="parent" style="--size: calc(100vw / {width});">
	{#each data as row}
		<div class="row">
			{#each row as cell}
				<div class="centered cell">
					<div class={`inner-cell ${cellTypeToString(cell)}`} />
				</div>
			{/each}
		</div>
	{/each}
</div>

<style lang="sass">
	.row
		display: flex

	.cell
		width: var(--size)
		height: var(--size)
		background-color: var(--palette-white)
	
	.inner-cell
		width: 0
		height: 0
		transition: all 0.4s ease-in

	.alive
		width: calc(var(--size) - 4px)
		height: calc(var(--size) - 4px)
		background-color: var(--palette-dark-purple)
</style>
