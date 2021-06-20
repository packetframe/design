<script lang="ts">
  let userClasses: string = "";
  export { userClasses as class };
  export let inputClasses: string = "";
  export let placeholder: string = "";
  export let label: string = "";
  export let error: string = null;
  export let disabled: boolean = false;
  export let size: string = "default";
  export let icon: string = null;
  export let value: string = "";
  export let fixErrorHeight: boolean = true;
  export let textarea: boolean = false;

  let focus: boolean;

  const handleFocus = () => {
    focus = true;
  }

  const handleBlur = () => {
    focus = false;
  }

  // NOTE: Don't bind types unless you actually need dynamic input types.
  // Using restProps means you can set the type as a prop using just type="number" and it will stay that type for its lifespan
</script>

<style lang="scss" src="./Input.scss" global>
</style>

<!-- svelte-ignore a11y-label-has-associated-control -->
<label class="pf-input {userClasses}" class:focus class:error={$$slots.error || error}>
  {label}
  <div class="pf-input__wrapper">
    {#if icon}
    <span class="material-icons pf-input__icon">{icon}</span>
    {/if}
    {#if !textarea}
      <input
        class:disabled
        class:icon
        class="pf-input__main size-{size} {inputClasses}"
        {placeholder}
        {disabled}
        {...$$restProps}
        on:focus={handleFocus}
        on:blur={handleBlur}
        on:input
        on:change
        bind:value
      />
    {:else}
      <textarea
        class:disabled
        class:icon
        class="pf-input__main size-{size} {inputClasses}"
        {placeholder}
        {disabled}
        {...$$restProps}
        on:focus={handleFocus}
        on:blur={handleBlur}
        on:input
        on:change
        bind:value
      ></textarea>
    {/if}
  </div>
  {#if error || fixErrorHeight}
  <span class="pf-input__error">{error ? error : ""}</span>
  {/if}
  <slot name="error"></slot>
</label>
