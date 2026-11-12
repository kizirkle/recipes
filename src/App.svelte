<script>
  import Recipe from './lib/Recipe.svelte'

  async function getRecipes(){
    const url = "https://recipeapi.io/api/v1/recipes";
    try{
        const response = await fetch(url, {
            method: "GET",
            headers: {
                "X-API-Key": import.meta.env.VITE_RECIPE_KEY,
                "Content-Type": "application/json"
            }
        });
        if(!response.ok){
            throw new Error("API failed to be fetched.");
        }
        const result = await response.json();
        return result.data;
    }catch (e){
        console.log(e);
    }
  }
  const recipes = getRecipes();
  let activeRecipe = $state({});
  $inspect(activeRecipe, "active recipe changed to:" + activeRecipe)
</script>

<section>
  <ul>
    {#await recipes then recipes}
      {#each recipes as recipe, index} 
      <li>
        <button onclick={() => {activeRecipe = recipe}}>
          {index + 1}: {recipe.name}
        </button>
      </li>
      {/each}
    {/await}
  </ul>

</section>

<Recipe recipe={activeRecipe} />

