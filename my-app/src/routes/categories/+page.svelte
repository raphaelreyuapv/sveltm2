<script>
    let categories = [
      { id: 1, name: "Sports d'homme" },
      { id: 2, name: "Sports de femme" },
      { id: 3, name: "Sports collectif" },
      { id: 4, name: "Sports individuels" },
    ];
  </script>
  
  <h1>Product Categories</h1>
  <ul>
    {#each categories as category}
      <li>
        <a href={`/${category.id}`}>{category.name}</a>
      </li>
    {/each}
  </ul>
  