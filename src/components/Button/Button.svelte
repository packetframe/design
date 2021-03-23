<script lang="ts">
    
    let userClasses: string = '';
    export { userClasses as class };
    export let size: string = 'default';
    export let style: string = null;
    export let type: string = null;
    // export let rounded: boolean = false;
    export let disabled: boolean = null;
    export let filled: boolean = false;
    export let flat: boolean = false;
    export let icon: string = null;
    export let href: string = null;
    export let ref: HTMLElement = null;
    export let variant: string = null;
</script>

<style lang="scss" src="./Button.scss" global>
</style>

{#if href}
    <a
        bind:this={ref}
        {href}
        class="pf-btn size-{size} {userClasses}"
        class:icon
        class:disabled
        class:filled
        class:flat
        class:secondary={variant == "secondary"}
        {style}
        {...$$restProps}
    >
        {#if icon}
            <span class="pf-btn__icon material-icons">{icon}</span>
        {/if}
        <span class="pf-btn__content">
            <slot></slot>
        </span>
    </a>
{:else}
    <button
        bind:this={ref}
        class="pf-btn size-{size} {userClasses}"
        class:icon
        class:disabled
        class:filled
        class:flat
        class:secondary={variant == "secondary"}
        {type}
        {style}
        {disabled}
        on:click
        on:dblclick
        {...$$restProps}
    >
        {#if icon}
            <span class="pf-btn__icon material-icons">{icon}</span>
        {/if}
        <span class="pf-btn__content">
            <slot></slot>
        </span>
    </button>
{/if}