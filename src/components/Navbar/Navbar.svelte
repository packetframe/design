<script lang="ts">
    import {location, link} from "svelte-spa-router";
    import active from "svelte-spa-router/active";

    export const elements = [
        {label: "DNS", href: "/dashboard/dns"},
        {label: "Containers", href: "/dashboard/containers"},
        {label: "Account", href: "/dashboard/account"}
    ];

    let open = true;
	let width;

	$: if ($location !== "") {
		open = false;
	}
	
	$: if (width > 825) {
		open = false;
	}
</script>

<svelte:window bind:innerWidth={width}></svelte:window>


<nav class="pf-nav">
    <a href="/"><img src="/images/logo.png" alt="Logo" /></a>
    <ul class:open>
        {#each elements as item}
            <li use:active={item.href}>
                <a href={item.href} use:link >{item.label}</a>
            </li>
        {/each}
    </ul>
    <span class="nav-expand" class:open></span>
    <span class="material-icons" on:click={() => open = !open} class:open>
        {open ? 'close' : 'menu'}
    </span>
</nav>

<style global lang="scss" src="./Navbar.scss">
</style>
