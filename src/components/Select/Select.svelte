<script>
  import Select from "svelte-select";

  export let items;
  export let label = "";
  export let showIndicator = true;
  export let isClearable = false;
  export let icon = null;
  export let selectedValue = null;
  export let isDisabled = false;

  import Icon from "./Icon.svelte";
</script>

<style lang="scss" src="./Select.scss" global>
</style>

<label class="pf-select" style="{label === '' ? '': 'padding-bottom: 19px;'}">
  <div class="pf-select__label">{label}</div>
  <Select Icon={icon ? Icon : null} iconProps={icon ? {icon} : null} {items} {isClearable} {isDisabled} showIndicator={showIndicator && !isDisabled} {selectedValue} on:select {$$restProps} />
</label>
