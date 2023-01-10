<script lang="ts">
	/**
	 * Wild HTML
	 * =====================
	 * Svelte Page
	 *
	 * @contributors: Patryk Rzucidło [@ptkdev] <support@ptkdev.io> (https://ptk.dev)
	 *
	 * @license: MIT License
	 *
	 */
	import Menu from "@components/common/menu/menu.svelte";
	import Footer from "@components/common/footer/footer.svelte";
	import { translate } from "@app/translations/translate";
	import { things } from "@app/types/global.interfaces";
	export let params = { wild: "" };
	let thething = things[Number(params.wild)];
	let recommendations: { recValue: Number; item: any }[] = [];
	things.forEach((element) => {
		//d(P1,P2)=squrt((sum(P2cord-P1cord)²)),repeat for all dimensions
		if (element.recommendation === undefined) {
			throw new TypeError("element Missing recommendation array??");
		}
		if (thething.recommendation === undefined) {
			throw new TypeError("target Missing recommendation array??");
		} //I fucking hate typescript
		let distofel = 0;
		for (let i = 0; i < element.recommendation.length; i++) {
			distofel += Math.pow(element.recommendation[i] - thething.recommendation[i], 2);
		}
		distofel = Math.sqrt(distofel);
		recommendations.push({ recValue: Number(distofel), item: element }); //insert distance with item
	});

	recommendations.sort((a, b) => (a.recValue > b.recValue ? -1 : 1)); //descending sort
</script>

<Menu />

<div id="container">
	<section class="hero is-medium is-primary is-bold">
		<div class="hero-body">
			<div class="container">
				<h1 class="title">{thething.name}</h1>
				<img src={thething.pngpath} alt="?" />
				<p>{thething.price}€</p>
			</div>
		</div>
	</section>
	<div class="content has-text-centered" />
	{#each recommendations as rec}
		<h1 class="title">{rec.item.name}</h1>
		<img src={rec.item.pngpath} alt="?" />
		<p>{rec.item.price}€</p>
		<p>Valeur de recommendation:{rec.recValue}</p>
	{/each}
</div>

<Footer />

<style lang="scss">
	@import "./wild.scss";
</style>
