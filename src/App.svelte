<script>
    import one from "./1.svelte";
    import two from "./2.svelte";
    import Router from 'svelte-spa-router'
    import three from "./3.svelte";


    const routes = {
        '/': one,
        '/cake' : two,
        '/gift' : three,
    }
</script>
<Router {routes}/>
