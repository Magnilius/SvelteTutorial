<script context="module"> 
    //API híváskor mindig ezt a context="Modulet használjuk"
   export async function load({fetch}) {
        const res = await fetch(
            "https://api.themoviedb.org/3/movie/popular?api_key=<APIKEY>&language=en-US&page=1"
            ); // meghívjuk a lekérdezést az adott linkről
        const data = await res.json(); //A lekérdezés eredményét jsonbe rakjuk
        if (res.ok) {
            return {
                props: {popular: data.results} //Publikusan elérhetővé tesszük a lekérdezett adatokat
            }
        }
   } 
</script>

<script>
    import PopularMovies from "../components/PopularMovies.svelte";
    import SearchMovies from "../components/SearchMovies.svelte";
    export let popular; // az elérhető adatokat beolvassuk és eltároljuk egy változóba
    import {fly} from 'svelte/transition';
</script>

<section in:fly= {{y: 50, duration: 500, delay: 500}} out:fly= {{y: 50, duration: 500}}>
    <SearchMovies />
    <PopularMovies  {popular}/>
</section>