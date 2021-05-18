<script lang="ts">
  import Input from "../Input";

  export let type = "A";

  let data = {
    labelA: "test"
  }
</script>

<style lang="scss" src="./RecordField.scss" global></style>

<main>
  {#if type === "A"}
    <Input bind:value={data.labelA} label="Label" />
    <Input label="IPv4 Address" />
  {:else if type === "A"}
    <Input label="Label" />
    <Input label="IPv6 Address" />
  {:else if type === "MX"}
    <Input label="Label" />
    <Input label="Server" />
    <Input label="Priority" />
  {:else if type === "NS"}
    <Input label="Label" />
    <Input label="Nameserver" />
  {:else if type === "TXT"}
    <Input label="Label" />
    <Input label="Value" />
  {/if}
</main>
