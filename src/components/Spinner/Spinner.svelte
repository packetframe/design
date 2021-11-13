<script lang="ts">

</script>


<div class="pf-spinner">
    <img class="pf-spinner__img" src="cloud-flat.png" width="81px" height="53px" alt="logo-spinner" />
    {#each [0, 1, 2] as _, i}
        <div class="pf-spinner__line" style="--delay:{i/2}s"></div>
    {/each}
</div>


<style lang="scss" src="./Spinner.scss" global>
</style>
