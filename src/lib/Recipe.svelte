<script>
    let {recipe} = $props();
    $inspect(recipe)
</script>

<section>
    <h2>{recipe.name}</h2>
    <ul>
        {#each recipe.dietary_tags as tag, index}
        <li>
            <p>{tag}</p>
        </li>
        {/each}
    </ul>
    <div>
        <div>
            <p>Difficulty:</p>
            <p>{recipe.difficulty}</p>

        </div>
        <div>
            <p>Cook Time:</p>
            <p>{recipe.cook_time}</p>

        </div>
        <div>
            <p>Calories:</p>
            <p>{recipe.calories_per_serving}</p>
        </div>
    </div>
    
    <p>{recipe.description}</p>
    <ul>
        {#each recipe.ingredients as ingredient, index}
        <li>
            <p>{ingredient.quantity}{ingredient.unit} {ingredient.name}</p>
        </li>
        {/each}
    </ul>
    <ul>
        {#each recipe.instructions as instruction, index}
        <li>
            <p>{instruction}</p>
        </li>
        {/each}
    </ul>
</section>