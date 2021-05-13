<script>
  import Select from "svelte-select";
  export let items;
  export let showIndicator = true;
  export let isClearable = false;
  export let icon = null;

  import AddIcon from './AddIcon.svelte';
</script>

<style lang="scss" src="./Select.scss" global>
</style>

<div class="pf-select" class:icon>
  <Select Icon={icon ? AddIcon : null} {items} {isClearable} {showIndicator} on:select {$$restProps}></Select>
</div>