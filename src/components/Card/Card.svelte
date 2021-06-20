<script lang="ts">
    export let title = "";
</script>

<main>
    <fieldset>
        <legend>{title}</legend>
        <slot></slot>
    </fieldset>
</main>

<style global lang="scss" src="./Card.scss">
</style>
