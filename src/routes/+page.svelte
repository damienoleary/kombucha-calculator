<script lang="ts">
	let liters = 0;
	$: normalisedLiters = liters > 100 || liters < 1 ? 1 : liters;
	$: teaConcentrateRaw = Math.round(normalisedLiters * 235);
	$: teaConcentrate = format(teaConcentrateRaw);
	$: coolWaterRaw = Math.round(normalisedLiters * 705);
	$: coolWater = format(coolWaterRaw);
	$: totalWater = format(parseInt(teaConcentrate) + parseInt(coolWater));
	$: teaBags = format(Math.max(1, Math.round(normalisedLiters * 1.5)));
	$: sugar = format(Math.round(normalisedLiters * 50));
	$: starterLiquid = format(Math.round(normalisedLiters * 60));
	$: scobySize = format(normalisedLiters * 28.3);

	function format(val: number) {
		return Intl.NumberFormat().format(val);
	}
</script>

<div class="container">
	<h1>Kombucha Recipe</h1>
	<div class="recipe">
		<div>
			<div>Liters:</div>
			<div><input type="number" max="100" min="1" bind:value={liters} /></div>
		</div>
		<div>
			<div>Tea Concentrate:</div>
			<div>{teaConcentrate} ml</div>
		</div>
		<div>
			<div>Cool water:</div>
			<div>{coolWater} ml</div>
		</div>
		<div>
			<div>Total water:</div>
			<div>{totalWater} ml</div>
		</div>
		<div>
			<div>Tea bags:</div>
			<div>{teaBags}</div>
		</div>
		<div>
			<div>Sugar:</div>
			<div>{sugar} g</div>
		</div>
		<div>
			<div>Starter Liquid:</div>
			<div>{starterLiquid} ml</div>
		</div>
		<div>
			<div>Scoby Size:</div>
			<div>{scobySize} g</div>
		</div>
	</div>
</div>

<style>
	div.container {
		margin: 0;
		padding: 2em;
	}

	div.recipe {
		display: flex;
		flex-wrap: wrap;
		justify-content: space-between;
		width: 56em;
		margin: 0 auto;
	}

	div.recipe > div {
		width: 20em;
		padding: 2em;
		justify-content: space-between;
		display: flex;
	}

	div.recipe > div > div {
		width: 6em;
	}

	div.recipe > div > div:nth-child(1) {
		flex-grow: 1;
	}

	div.recipe > div > div:nth-child(2) {
		text-align: right;
	}

	div.recipe > div > div:nth-child(2) > input {
		width: 3em;
		font-size: 1em;
	}

	h1 {
		text-align: center;
	}
</style>
