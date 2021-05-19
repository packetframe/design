<script lang="ts">
  import Input from "../Input";
  import Button from "../Button";
  import Select from "../Select/Select.svelte";
  import { onMount } from "svelte";

  export let record = {
    label: "",
    ttl: 86400,
    value: "",
    proxied: false
  };
  export let type = "A";
  export let isInDropdown = false;

  let recordTypes = [
    { value: "A", label: "A" },
    { value: "AAAA", label: "AAAA" },
    { value: "MX", label: "MX" },
    { value: "NS", label: "NS" },
    { value: "TXT", label: "TXT" }
  ];

  // If the component is in the record edit dropdown, set a static record type
  onMount(() => {
    if (isInDropdown) {
      recordTypes = [{ value: type, label: type }];
    }
  });

  function handleRecordSelect(event) {
    type = event.detail.value;
  }
</script>

<style lang="scss" src="./RecordField.scss" global></style>

<div class="pf-record-field">
  <Input bind:value={record.label} label="Label" />
  <span class="pf-record-field__small-select"><Select label="Type" items={recordTypes} on:select={handleRecordSelect} bind:selectedValue={recordTypes[0]} isDisabled={isInDropdown} /></span>
  <Input class="small" type="number" label="TTL" placeholder="86400" min="0" bind:value={record.ttl} />

  {#if type === "A"}
    <Input bind:value={record.value} label="IPv4 Address" />
  {:else if type === "AAAA"}
    <Input bind:value={record.value} label="IPv6 Address" />
  {:else if type === "MX"}
    <Input bind:value={record.value} label="Server" />
    <Input bind:value={record.value} type="number" label="Priority" min="0" />
  {:else if type === "NS"}
    <Input bind:value={record.value} label="Nameserver" />
  {:else if type === "TXT"}
    <Input bind:value={record.value} label="Value" />
  {/if}
  <Button variant="secondary" icon={record.proxied ? "cloud_queue" : "cloud_off"} on:click={() => record.proxied = !record.proxied} class="ma-2" />
  <Button variant="secondary" class="ma-2">Save</Button>
</div>
