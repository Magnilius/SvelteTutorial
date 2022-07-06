<script>
    let inputValue = '';
    let active = false;
    
    import {goto} from '$app/navigation';
    import {fly} from 'svelte/transition';


    function cancelInactive() {
        if (inputValue) {
            active = true;
        } else {
            active = false;
        }
    }

    function submitSearch () {
        goto("/search/"+inputValue);
    }
</script>

<form on:submit|preventDefault={submitSearch} class="search"><!--on:submit form beküldésekor mit csináljon || |preventDefault e.preventDefault() rövidebben-->

    {#if  !active}
    <label in:fly= {{y: -10, duration: 500}} out:fly= {{y: -10, duration: 500}} for="search_movie">Search Movie</label> <!--in:fly out:fly sveltbe épített animációk-->
    {/if}
    <input 
    on:blur={cancelInactive}
    on:focus={()=> (active = true)} 
    bind:value={inputValue} 
    type="text" 
    name="search_movie"
    class = {active ? 'selected' : ''} />
    <!--bind:value={változó} paranccsal értéket tudunk adni egy js változónak az inputtal 
    || on:focus kiválasztáskor átálítja az értékét az activenak 
    || on:blur nem aktív esetén változtat értéket
    || classba egyszerűen megvizsgáljuk hogy van e érték és úgy állítjuk a css osztályát dinamikusan -->
    {#if inputValue}
        <button in:fly= {{x: 0, duration: 500}} out:fly= {{x: 0, duration: 500}}>Search</button>
    {/if}
    
</form>

<style>

    .search {
        position: relative;
        widows: 30%;
        margin: 1rem;
    }
    button {
        font-size: 0.7rem;
        padding: 0rem 1rem;
        background-color: rgb(96,110,201);
        color: white;
        font-weight: bold;
        border: none;
        position: absolute;
        bottom: 50%;
        right: 0;
        transform: translate(0, 50%);
        height: 100%;
        border-top-right-radius: 10px;
        border-bottom-right-radius: 10px;
        cursor: pointer;
    }
    input {
        width: 100%;
        border: none;
        font-size: 1rem;
        font-family: 'Courier New', Courier, monospace;
        outline: none;
        color: rgb(255, 255, 255);
        padding: 0.5rem 0.1rem;
        transition: background 0.75s ease-out;
        font-weight: bold;
        background: rgb(63, 63, 63);
        border-radius: 10px;
        padding: 1rem;
    }
    label {
        position: absolute;
        font-size: 0.8rem;
        top: 50%;
        left: 0;
        transform: translate(0, -50%);
        pointer-events: none;
        color: #fff;
        padding: 0rem 1rem;
    }
    input.selected {
        background-color: rgb(50, 50, 50);
    }
</style>