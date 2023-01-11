
<script>
    import {Router,Route} from "svelte-routing";
    import { page } from '$app/stores';
    let items = [
      { id: 1, name: "Item 1" },
      { id: 2, name: "Item 2" },
      { id: 3, name: "Item 3" },
    ];
    //CSPplus:0,CSPmoins:0,homme:0,femme:0,vieux(>40 ans):0,jeune:0,individuel:0,collectif:0, débutant:0, expérimenté:0, 
//   enfant:0, aventurier, combatif, competitif, fitness, artistique
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

    things.sort((a,b) => a.recommendation[$page.params.slug] > b.recommendation[$page.params.slug] ? -1 : 1);
  </script>
  <meta name="viewport" content="width=device-width,initial-scale=1">

  <body>
  <div id="container">
	<section class="hero is-medium is-primary is-bold">
		<div class="hero-body">
			<div>
				{#each things as thing}
					<div class="container">
						<h1 class="name">{thing.name}</h1>
						<h2 class="price">{thing.price}€</h2>
						<a href={"/item/"+thing.id}><img src={"/images/"+thing.pngpath} alt="item" /></a>
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
</body>

<style>
 .container{
    display:flex;
    flex-direction: row;
    align-items: center;
    gap:50px 50px;
    flex:auto;
}
body {
    background: linear-gradient(to bottom, #000033, #000000); /* background gradient from blue to black */
    color: white; /* text color is white to increase contrast */
}

ul {
    width: 80%;
    margin: 0 auto;
    list-style: none;
}

li {
    display: flex;
    align-items: center;
    background-color: rgba(255,255,255,0.5); /* make the background of list item semi-transparent */
    padding: 20px;
    margin-bottom: 10px;
    box-shadow: 0px 0px 5px 0px #ccc;
}

img {
    width: 100px;
    height: 100px;
    margin-right: 20px;
}

.name {
    font-size: 18px;
    font-weight: bold;
}

.price {
    font-size: 14px;
    color: green;
    margin-left: auto;
}
@media only screen and (max-width: 600px) {
    body {
        font-size: 14px;
    }
}

</style>