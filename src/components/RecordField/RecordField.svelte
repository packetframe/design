<script lang="ts">
    import Input from "../Input";
    import Button from "../Button";
    import Select from "../Select";
    import {onMount} from "svelte";

    export let record = {
        label: "",
        ttl: 86400,
        value: "",
        proxied: false
    };
    export let type = "A";
    export let isInDropdown = false;
    export let mobile = false;

    let recordTypes = [
        {value: "A", label: "A"},
        {value: "AAAA", label: "AAAA"},
        {value: "MX", label: "MX"},
        {value: "TXT", label: "TXT"},
        {value: "NS", label: "NS"},
        {value: "SRV", label: "SRV"}
    ];

    // If the component is in the record edit dropdown, set a static record type
    onMount(() => {
        if (isInDropdown) {
            recordTypes = [{value: type, label: type}];
        }
    });

    function handleRecordSelect(event) {
        type = event.detail.value;
    }

    // Record values
    let priority = 0;
    let weight = 0;
    let port = 0;
</script>

<style global lang="scss" src="./RecordField.scss">
</style>

<div class="pf-record-field" class:mobile>
    <div class="pf-record-field__row">
        <Input bind:value={record.label} label="Label"/>
        <span class="pf-record-field__small-select">
            <Select bind:selectedValue={recordTypes[0]} isDisabled={isInDropdown}
                    items={recordTypes}
                    label="Type"
                    on:select={handleRecordSelect}/>
        </span>
        <Input bind:value={record.ttl} class="small" label="TTL" min="0" placeholder="86400" type="number"/>

        {#if type === "A"}
            <Input bind:value={record.value} label="IPv4 Address"/>
        {:else if type === "AAAA"}
            <Input bind:value={record.value} label="IPv6 Address"/>
        {:else if type === "MX"}
            <Input class="small" type="number" label="Priority" min="0"/>
            <Input bind:value={record.value} label="Server"/>
        {:else if type === "NS"}
            <Input bind:value={record.value} label="Nameserver"/>
        {:else if type === "TXT"}
            <Input bind:value={record.value} label="Value"/>
        {:else if type === "SRV"}
            <Input class="small" type="number" label="Priority" min="0" bind:selectedValue={priority}/>
            <Input class="small" type="number" label="Weight" min="0" bind:selectedValue={weight}/>
            <Input class="small" type="number" label="Port" min="0" bind:selectedValue={port}/>
            <Input bind:value={record.value} label="Target"/>
        {/if}
        <Button icon={record.proxied ? "cloud_queue" : "cloud_off"} on:click={() => record.proxied = !record.proxied}
                variant="secondary"/>
        <Button variant="secondary">{isInDropdown ? "Save" : "Add"}</Button>
        {#if mobile}
        <Button danger icon="delete_outline" on:click={() => alert("Are you sure you want to delete this record?")} />
        {/if}
    </div>
</div>
