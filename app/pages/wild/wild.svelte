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
</div>

<Footer />

<style lang="scss">
	@import "./wild.scss";
</style>
