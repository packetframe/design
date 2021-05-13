<script>
import { onMount } from "svelte";

  import Select from "svelte-select";
  export let items;
  export let showIndicator = true;
  export let isClearable = false;
  export let icon = null;

  import Icon from './Icon.svelte';
  onMount(() => {
    if (icon) {
      document.getElementById("pf-select-icon").innerText = icon;
    }
  })
</script>

<style lang="scss" src="./Select.scss" global>
</style>

<div class="pf-select" class:icon>
  <Select Icon={icon ? Icon : null} {items} {isClearable} {showIndicator} on:select {$$restProps}></Select>
</div>