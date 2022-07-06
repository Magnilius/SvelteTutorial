<script>
    export let popular;
    import MovieCard from "./MovieCard.svelte";
    import {fly} from 'svelte/transition';
</script>

<h3>Popular Movies</h3>
<div class="popular-movies">
    {#each popular as movie} <!--Svelte foreach-->
       <MovieCard {movie}/> <!--Rendrelem a komponenst majd a {}-ba átadom a megfelelő változó paraméterét-->
    {/each}
</div>

<style>
    h3 {
        padding:  0 1rem;
    }
    .popular-movies {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
        grid-column-gap: 1rem;
        grid-row-gap: 2rem;
    }
</style>