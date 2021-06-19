<script>
  import {location} from "svelte-spa-router";

  const elements = [
    { label: "DNS", href: "/dashboard/dns" },
    { label: "Containers", href: "/dashboard/containers" },
    { label: "Proxy", href: "/dashboard/proxy" },
    { label: "Account", href: "/dashboard/account" }
  ];
</script>

<nav class="pf-nav">
  <ul>
    {#each elements as item}
      <li class={$location === item.href ? "active" : ""}>
        <a href={"#" + item.href}>{item.label}</a>
      </li>
    {/each}
  </ul>
</nav>

<style lang="scss" src="./Navbar.scss" global>
</style>
