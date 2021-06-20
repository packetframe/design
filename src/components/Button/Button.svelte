<script lang="ts">
    let userClasses: string = '';
    export {userClasses as class};
    export let size: string = 'default';
    export let style: string = null;
    export let type: string = null;
    // export let rounded: boolean = false;
    export let disabled: boolean = null;
    export let icon: string = null;
    export let href: string = null;
    export let ref: HTMLElement = null;
    export let danger: boolean = null;
    export let variant: null | "filled" | "flat" | "secondary" = null;
    export let iconStyle: string = "";
</script>

<style global lang="scss" src="./Button.scss">
</style>

{#if href}
    <a
            bind:this={ref}
            {href}
            class="pf-btn size-{size} {userClasses}"
            class:icon
            class:disabled
            class:danger
            class:default={variant === null}
            class:filled={variant === "filled"}
            class:flat={variant === "flat"}
            class:secondary={variant === "secondary"}
            {style}
            {...$$restProps}
    >
        {#if icon}
            <span class="pf-btn__icon material-icons" class:iconOnly={!$$slots.default}>{icon}</span>
        {/if}
        {#if $$slots.default}
            <span class="pf-btn__content">
                <slot></slot>
            </span>
        {/if}
    </a>
{:else}
    <button
            bind:this={ref}
            class="pf-btn size-{size} {userClasses}"
            class:icon
            class:disabled
            class:danger
            class:default={variant === null}
            class:filled={variant === "filled"}
            class:flat={variant === "flat"}
            class:secondary={variant === "secondary"}
            {type}
            {style}
            {disabled}
            on:click
            on:dblclick
            {...$$restProps}
    >
        {#if icon}
            <span class="pf-btn__icon material-icons" style={iconStyle} class:iconOnly={!$$slots.default}>{icon}</span>
        {/if}
        {#if $$slots.default}
            <span class="pf-btn__content">
                <slot></slot>
            </span>
        {/if}
    </button>
{/if}
