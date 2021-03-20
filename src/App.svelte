<script lang="ts">
  import Router from "svelte-spa-router";

  import Index from "./demo/pages/Index.svelte";

  const routes = {
    "/": Index
  };
</script>

<main>
  <Router {routes} />
</main>

<style lang="scss">
  main {
    width: 100%;
    min-height: 100vh;
    margin: 0;
  }
</style>