<script lang="ts">
  export let title: string = "";
</script>

<style lang="scss" src="./Table.scss" global />

<main>
  <div>
    <h2>{title}</h2>
    <span>
      <slot name="header" />
    </span>
  </div>

  <table>
    <slot />
  </table>
</main>
