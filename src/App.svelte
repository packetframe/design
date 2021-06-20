<script lang="ts">
    import Router, {push, location} from "svelte-spa-router";

    import Navbar from "./components/Navbar/Navbar.svelte";

    import Index from "./demo/pages/Index.svelte";
    import DNS from "./demo/pages/dashboard/DNS.svelte";
    import Containers from "./demo/pages/dashboard/Containers.svelte";
    import Account from "./demo/pages/dashboard/Account.svelte";

    $: {
        if ($location === "/dashboard") {
            push("/dashboard/dns")
        }
    }

    const routes = {
        "/": Index,
        "/dashboard/dns": DNS,
        "/dashboard/containers": Containers,
        "/dashboard/account": Account
    };
</script>

<main class="pf-app">
    <Navbar/>
    <Router {routes}/>
    <footer>&copy; Packetframe 2021</footer>
</main>

<style global lang="scss">
  @import './styles/global';

  .pf-app {
    width: 100%;
    min-height: 100vh;
    margin: 0;
  }

  footer {
    margin: 15px;
    color: white;
    text-align: center;
  }
</style>
