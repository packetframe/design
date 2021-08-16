<script lang="ts">
    export let title = "";
</script>

<div class="pf-card">
    <h3 class="pf-card__header">{title}</h3>
    <slot></slot>
</div>

<style global lang="scss" src="./Card.scss">
</style>
