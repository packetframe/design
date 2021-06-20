<script>
    import Input from "../Input";
    import Card from "../Card/Card.svelte";
    import Button from "../Button/Button.svelte";

    export let values = [];

    let value;
</script>

<main>
    <Card title="Ports">
        <div style="display: flex; align-items: center">
            <Input label="Ports" placeholder="443:443" bind:value/>
            <Button icon="add" on:click={() => {
                values.push(value)
                alert(values)
            }}/>
        </div>

        <span>Ports: (click to delete) {values}</span>

        {#if values.length > 0}
            <ul>
                {#each values as item}
                    <li>{item}</li>
                {/each}
            </ul>
        {/if}
    </Card>
</main>
