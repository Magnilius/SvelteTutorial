<script>
     import global from "../global.css"
     import Nav from "../components/Nav.svelte";
</script>


<svelte:head>
    <title>Movie Db</title>
</svelte:head>

<Nav />

<slot /> <!--Ezt hozzáadva ez egy minden aloldalra behivatkozott komponens lesz-->