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
    import { page } from '$app/stores';
    const things = [
    {id:0, name: 'Club de golf',pngpath:'golf.jpg',price:49,recommendation:[99,0,99,50,99,0,99,0,99,99,0,0,0,70,0,0]},
    {id:1, name: 'Tapis de yoga',pngpath:'souris.jpg',price:29,recommendation:[20,40,0,97,10,45,45,75,99,70,0,0,0,0,99,0]},
    {id:2,name: 'Chassures de course',pngpath:'course.jpg',price:59,recommendation:[50,75,75,50,0,50,99,0,99,50,0,0,0,99,90,0]},
    {id:3,name: 'Trampoline',pngpath:'trampo.jpg',price:999,recommendation:[99,20,45,33,0,70,0,90,99,0,99,0,0,0,0,0]},
    {id:4,name: 'Raquette de Tenis',pngpath:'tennis.jpg',price:99,recommendation:[95,30,50,70,20,80,45,45,0,99,0,0,0,99,0,0]},
    {id:5,name: 'Chaussons de danse femme',pngpath:'danse.png',price:10,recommendation:[75,25,0,99,10,90,90,10,99,0,0,0,0,99,0,99]},
    {id:6,name: 'Planche de surf',pngpath:'planchesurf.png',price:260,recommendation:[60,40,70,30,0,99,99,0,0,99,0,90,0,99,60,30]},
    {id:7,name: 'Ballon de foot Adidas',pngpath:'ballonfootadadidascheap.png',price:9,recommendation:[0,99,80,20,10,90,0,99,99,30,10,0,0,80,0,0]},
    {id:8,name: 'Ballon de foot Adidas ULC League',pngpath:'ballonfootadadidasleague.png',price:40,recommendation:[99,0,80,20,10,90,0,99,45,99,0,0,0,99,0,0]},
    {id:9,name: 'Justaucorps de danse pour fille',pngpath:'justaucorpsdanseenfantfille.png',price:15,recommendation:[90,99,0,99,0,99,99,0,99,30,99,0,0,70,90,99]},
    {id:10,name: 'Kit de danse classique pour fille',pngpath:'ensembledanseenfantfille.png',price:50,recommendation:[0,99,0,99,0,99,99,40,99,0,99,0,0,90,0,99]},
    {id:11,name: 'Robe de danse latine',pngpath:'femmerobedanselatine.png',price:60,recommendation:[99,45,0,99,45,99,10,99,0,99,0,0,0,99,0,99]},
    {id:12,name: 'Patins à roulette femme',pngpath:'patinsroulette.png',price:45,recommendation:[75,25,0,99,0,99,99,0,99,55,0,0,0,70,0,70]},
    {id:13,name: 'Patins à glace homme',pngpath:'patinsglacehomme.png',price:35,recommendation:[70,40,99,0,0,99,99,45,0,99,0,0,0,99,0,55]},
    {id:14,name: 'Short de tennis homme',pngpath:'shorttennishomme.png',price:9,recommendation:[99,0,99,0,99,0,99,0,99,0,0,0,0,99,0,0]},
    {id:15,name: 'Ensemble de tennis enfant',pngpath:'tenuetennisenfant.png',price:40,recommendation:[99,0,99,0,0,99,99,0,99,0,99,0,0,99,0,0]},
    {id:16,name: 'Poignée alpinisme professionnel',pngpath:'poigneealpinismepro.png',price:70,recommendation:[50,50,55,45,10,90,99,0,0,99,0,99,0,70,0,0]},
    {id:17,name: 'Kit escalade enfant',pngpath:'kitescaladeenfant.jpg',price:100,recommendation:[50,50,55,45,0,99,99,0,99,0,99,99,0,99,0,0]},
    {id:18,name: 'Vélo',pngpath:'velo.png',price:500,recommendation:[99,0,99,0,45,70,99,0,0,99,0,70,0,99,0,0]},
    {id:19,name: 'Kimono',pngpath:'kimono.png',price:45,recommendation:[45,55,99,0,45,99,99,0,99,55,0,0,99,70,0,0]},
    {id:20,name: 'Gants de boxe',pngpath:'gantsboxe.png',price:40,recommendation:[10,99,99,30,10,99,99,0,0,99,0,0,99,99,0,0]},
];
	let thething = things[Number($page.params.slug)];
	let recommendations = [];
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


<div id="container">
	<section class="hero is-medium is-primary is-bold">
		<div class="hero-body">
			<div class="container">
				<h1 class="title">{thething.name}</h1>
				<img src={"/images/"+thething.pngpath} alt="?" />
				<p>{thething.price}€</p>
			</div>
		</div>
	</section>
	<div class="content has-text-centered" />
	{#each recommendations as rec}
		<h1 class="title">{rec.item.name}</h1>
		<a href={rec.item.id} data-sveltekit-reload rel="external">
			<img src={"/images/"+rec.item.pngpath} alt="?" /></a
		>
		<p>{rec.item.price}€</p>
		<p>Valeur de recommendation:{rec.recValue}</p>
	{/each}
</div>
