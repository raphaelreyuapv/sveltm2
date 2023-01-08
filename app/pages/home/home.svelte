<script lang="ts">
	/**
	 * Home HTML
	 * =====================
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
</script>

<Menu />

<div id="container">
	<section class="hero is-medium is-primary is-bold">
		<div class="hero-body">
			<div class="container">
				{#each things as thing}
					<h1 class="title">{thing.name}</h1>
					<h2 class="subtitle">{thing.price}</h2>
					<img src={thing.pngpath} alt="club de golf lol" />
					<a href={"#/wild/" + thing.id}>Go</a>
				{/each}
			</div>
		</div>
	</section>
	<div class="content has-text-centered">app/pages/home.svelte</div>
</div>

<Footer />

<style lang="scss">
	@import "./home.scss";
</style>
