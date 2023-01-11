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
			<div>
				{#each things as thing}
					<div class="container">
						<h1 class="title">{thing.name}</h1>
						<h2 class="subtitle">{thing.price}€</h2>
						<a href={"#/wild/" + thing.id}><img src={thing.pngpath} alt="club de golf lol" /></a>
						<div class="innercontainer">
							<p>axe CSP plus {thing.recommendation[0]}</p>
							<p>axe CSP moins {thing.recommendation[1]}</p>
							<p>axe homme {thing.recommendation[2]}</p>
							<p>axe femme {thing.recommendation[3]}</p>
							<p>axe vieux {thing.recommendation[4]}</p>
							<p>axe jeune {thing.recommendation[5]}</p>
							<p>axe individuel {thing.recommendation[6]}</p>
							<p>axe collectif {thing.recommendation[7]}</p>
							<p>axe debutant {thing.recommendation[8]}</p>
							<p>axe experimente {thing.recommendation[9]}</p>
							<p>axe enfant {thing.recommendation[10]}</p>
							<p>axe aventurier {thing.recommendation[11]}</p>
							<p>axe combatif {thing.recommendation[12]}</p>
							<p>axe competitif {thing.recommendation[13]}</p>
							<p>axe fitness {thing.recommendation[14]}</p>
							<p>axe artistique {thing.recommendation[15]}</p>
						</div>
					</div>
				{/each}
			</div>
		</div>
	</section>
</div>

<Footer />

<style lang="scss">
	@import "./home.scss";
</style>
