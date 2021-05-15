<script lang="ts">
  import Router from "svelte-spa-router";

  import Index from "./demo/pages/Index.svelte";

  const routes = {
    "/": Index
  };
</script>

<main class="pf-app">
  <Router {routes} />
</main>

<style lang="scss" global>
  @import './styles/global';
  .pf-app {
    width: 100%;
    min-height: 100vh;
    margin: 0;
  }
</style>