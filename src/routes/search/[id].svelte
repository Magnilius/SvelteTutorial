<script context="module"> 
    //API híváskor mindig ezt a context="Modulet használjuk"
   export async function load({fetch, params}) {
        const res = await fetch(
            "https://api.themoviedb.org/3/search/movie?api_key=<APIKEY>&language=en-US&page=1&query="+params.id+"&page=1&include_adult=false"
            ); // meghívjuk a lekérdezést az adott linkről
        const data = await res.json(); //A lekérdezés eredményét jsonbe rakjuk
        console.log(data)
        if (res.ok) {
            return {
                props: {searchedMovie : data.results} //Publikusan elérhetővé tesszük a lekérdezett adatokat
            }
        }
   } 
</script>

<script>
    import MovieCard from "../../components/MovieCard.svelte";
    export let searchedMovie;
    import {fly} from 'svelte/transition';
</script>

<div class="searched-movies">
    {#each searchedMovie as movie}
        <MovieCard {movie}/>
    {/each}
</div>

<style>
     .searched-movies {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
        grid-column-gap: 1rem;
        grid-row-gap: 2rem;
    }
</style>