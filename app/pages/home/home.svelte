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

	let searchString = '';
	let itemsVisible = false;

</script>

<Menu />

<div id="container">
	<ul id="menu">
		<li><a href="/" on:click|preventDefault={() => (menu = 1)}>Athlétisme</a></li> |
		<li><a href="/" on:click|preventDefault={() => (menu = 2)}>Aquatique</a></li> |
		<li><a href="/" on:click|preventDefault={() => (menu = 1)}>Artistique</a></li> |
		<li><a href="/" on:click|preventDefault={() => (menu = 2)}>Ballon</a></li> |
		<li><a href="/" on:click|preventDefault={() => (menu = 1)}>Combat</a></li> |
		<li><a href="/" on:click|preventDefault={() => (menu = 2)}>Fitness</a></li> |
		<li><a href="/" on:click|preventDefault={() => (menu = 1)}>Sports Extrêmes</a></li> |
		<li><a href="/" on:click|preventDefault={() => (menu = 2)}>Cyclisme</a></li>
	</ul>
	
	<input bind:value={searchString} placeholder="rechercher un produit">
	<button on:click="{() => searchString = searchString}">Chercher</button>
	<img src="mapImg.jpg" alt="carte du magasin" />

	<button on:click="{() => itemsVisible = !itemsVisible}">Voir tous nos produits</button>
	{#if itemsVisible}
	<section class="hero is-medium is-primary is-bold">
		<div class="hero-body">
			<div class="container">
				{#each things as thing}
					<h1 class="title">{thing.name}</h1>
					<h2 class="subtitle">{thing.price}€</h2>
					<img src={thing.pngpath} alt="club de golf lol" />
					<a href={"#/wild/" + thing.id}>Go</a>
				{/each}
			</div>
		</div>
	</section>
	<div class="content has-text-centered">app/pages/home.svelte</div>
	{/if}
</div>

<Footer />

<style lang="scss">
	@import "./home.scss";
	ul#menu li{
		display : inline;
	}
</style>
