<script>
    import {location} from "svelte-spa-router";
    import Select from "../Select/Select.svelte";

    let zones = ["example.com"];
    let zone = zones[0];

    const elements = [
        {label: "DNS", href: "/dashboard/dns"},
        {label: "Containers", href: "/dashboard/containers"},
        {label: "Account", href: "/dashboard/account"}
    ];
</script>

<div class="pf-navs">
    <!-- Left nav -->
    <nav class="pf-nav">
        <ul style="justify-content: flex-start">
            <img style="width: 230px" src="/images/logo.png" alt="Logo">
            <li><Select bind:selectedValue={zone} items={zones}/></li>
        </ul>
    </nav>

    <!-- Right nav -->
    <nav class="pf-nav">
        <ul>
            {#each elements as item}
                <li class={$location === item.href ? "active" : ""}>
                    <a href={"#" + item.href}>{item.label}</a>
                </li>
            {/each}
        </ul>
    </nav>
</div>

<style global lang="scss" src="./Navbar.scss">
</style>
