<script>
  import Select from "svelte-select";
  export let items;
</script>

<style lang="scss" src="./Select.scss" global>
</style>

<div class="pf-select">
  <Select {items} on:select {$$restProps}></Select>
</div>