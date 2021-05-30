<script>
  const elements = [
    { label: "DNS", href: "#", active: true },
    { label: "Containers", href: "#", active: false },
    { label: "Proxy", href: "#", active: false },
    { label: "Account", href: "#", active: false }
  ];
</script>

<nav class="pf-nav">
  <ul>
    {#each elements as item}
      <li class={item.active ? "active" : ""}>
        <a href={item.href}>{item.label}</a>
      </li>
    {/each}
  </ul>
</nav>

<style lang="scss" src="./Navbar.scss" global>
</style>
