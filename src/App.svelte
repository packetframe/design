<script lang="ts">
    import Router from "svelte-spa-router";
    const routes = {};
</script>

<main>
    <Router {routes}/>
</main>

<style lang="scss">
	$color: red;

	main {
		width: 100%;
		min-height: 100vh;
	}
</style>