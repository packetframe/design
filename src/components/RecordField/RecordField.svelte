<script lang="ts">
  import Input from "../Input";
  import Button from "../Button";

  export let type = "A";

  let recordPreview = "";

  let data = {
    labelA: "test"
  }
</script>

<style lang="scss" src="./RecordField.scss" global></style>

<div class="pf-record-field">
  {#if type === "A"}
    <Input bind:value={data.labelA} label="Label" />
    <Input label="IPv4 Address" />
  {:else if type === "AAAA"}
    <Input label="Label" />
    <Input label="IPv6 Address" />
  {:else if type === "MX"}
    <Input label="Label" />
    <Input label="Server" />
    <span class="constrain"><Input type="number" label="Priority" min="0" /></span>
  {:else if type === "NS"}
    <Input label="Label" />
    <Input label="Nameserver" />
  {:else if type === "TXT"}
    <Input label="Label" />
    <Input label="Value" />
  {/if}
  <Button variant="secondary" class="ma-2">Save</Button>
  <span>{recordPreview}</span>
</div>
