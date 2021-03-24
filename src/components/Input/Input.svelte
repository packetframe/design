<script lang="ts">
  let userClasses: string = '';
  export { userClasses as class };
  export let placeholder: string = "";
  export let label: string = "";
  export let error: string = null;
  export let disabled: boolean;
  export let size: string = "default";
</script>

<style lang="scss" src="./Input.scss" global>
</style>

<label class="pf-input">
  {label}
  <input 
    {placeholder}
    {disabled}
    class:disabled
    class="pf-input__main size-{size} {userClasses}"
  />
  <span class="pf-input__error">{error}</span>
  <slot name="error"></slot>
</label>

