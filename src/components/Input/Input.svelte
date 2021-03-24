<script lang="ts">
  let userClasses: string = "";
  export { userClasses as class };
  export let placeholder: string = "";
  export let label: string = "";
  export let error: string = null;
  export let disabled: boolean;
  export let size: string = "default";
  export let icon: string = null;
  export let value: string = "";
  
  let focus: boolean;

  const handleFocus = () => {
    focus = true;
  }

  const handleBlur = () => {
    focus = false;
  }


</script>

<style lang="scss" src="./Input.scss" global>
</style>

<label class="pf-input" class:focus>
  {label}
  {#if icon}
  <span class="material-icons pf-input__icon">{icon}</span>
  {/if}
  <input 
    class:disabled
    class:icon
    class="pf-input__main size-{size} {userClasses}"
    {placeholder}
    {disabled}
    {...$$restProps}
    on:focus={handleFocus}
    on:blur={handleBlur}
    on:input
    on:change
    bind:value
  />
  {#if error}
  <span class="pf-input__error">{error}</span>
  {/if}
  <slot name="error"></slot>
</label>

