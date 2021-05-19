<script lang="ts">
  import Input from "../Input";
  import Button from "../Button";
  import Select from "../Select/Select.svelte";
  import { onMount } from "svelte";

  export let type = "A";
  export let isInDropdown = false;

  let recordPreview = "";

  let data = {
    labelA: "test"
  };

  let recordTypes = [
    { value: "A", label: "A" },
    { value: "AAAA", label: "AAAA" },
    { value: "MX", label: "MX" },
    { value: "NS", label: "NS" },
    { value: "TXT", label: "TXT" }
  ];

  onMount(() => {
    if (isInDropdown) {
      recordTypes = [{ value: type, label: type }]
    }
  })

  function handleRecordSelect(event) {
    type = event.detail.value;
  }
</script>

<style lang="scss" src="./RecordField.scss" global></style>

<div class="pf-record-field">
  <Input bind:value={data.labelA} label="Label" />
  <span class="pf-record-field__small-select"><Select label="Type" items={recordTypes} on:select={handleRecordSelect} bind:selectedValue={recordTypes[0]} isDisabled={isInDropdown} /></span>
  <Input class="small" type="number" label="TTL" placeholder="86400" />

  {#if type === "A"}
    <Input label="IPv4 Address" />
  {:else if type === "AAAA"}
    <Input label="IPv6 Address" />
  {:else if type === "MX"}
    <Input label="Server" />
    <Input type="number" label="Priority" min="0" />
  {:else if type === "NS"}
    <Input label="Nameserver" />
  {:else if type === "TXT"}
    <Input label="Value" />
  {/if}
  <Button variant="secondary" class="ma-2">Save</Button>
  <span>{recordPreview}</span>
</div>
