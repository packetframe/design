<script>
  import Select from "svelte-select";
  export let items;
  export let showIndicator = true;
  export let isClearable = false;
</script>

<style lang="scss" src="./Select.scss" global>
</style>

<div class="pf-select">
  <Select {items} {isClearable} {showIndicator} on:select {$$restProps}></Select>
</div>