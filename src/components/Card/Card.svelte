<script lang="ts">
    export let title: string|null = null;
    export let width: string|null = null;
    let userClasses: string = "";
    export {userClasses as class};
</script>

<div class={`pf-card ${userClasses}`} style={width ? `--width:${width}` : ``}>
    {#if title}
    <h3 class="pf-card__header">{title}</h3>
    {/if}
    <slot></slot>
</div>

<style global lang="scss" src="./Card.scss">
</style>
