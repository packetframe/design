<script lang="ts">
  let userClasses: string = "";
  export { userClasses as class };
  export let placeholder: string = "";
  export let label: string = "";
  export let error: string = null;
  export let disabled: boolean = false;
  export let size: string = "default";
  export let icon: string = null;
  export let value: string = "";
  export let fixErrorHeight: boolean = true;
  export let number: boolean = false;

  let focus: boolean;

  const handleFocus = () => {
    focus = true;
  }

  const handleBlur = () => {
    focus = false;
  }

  // TODO: This should honor the number parameter, but type binding is a bit weird: https://github.com/sveltejs/svelte/issues/3921
</script>

<style lang="scss" src="./Input.scss" global>
</style>

<!-- svelte-ignore a11y-label-has-associated-control -->
<label class="pf-input" class:focus class:error={$$slots.error || error}>
  {label}
  <div class="pf-input__wrapper">
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
  </div>
  {#if error || fixErrorHeight}
  <span class="pf-input__error">{error ? error : ""}</span>
  {/if}
  <slot name="error"></slot>
</label>
