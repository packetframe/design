<script lang="ts">
  import Record from "../Record";

  type Record = {
    label: string,
    type: string,
    ttl: number,
    value: string,
    proxied: boolean,
  }

  export let allowDeletion: boolean = true;
  export let allowSelection: boolean = true;
  export let handleSelection: (selectionState: boolean, data: Record, e: MouseEvent) => any = () => {};
  export let handleDeletion: (data: Record[]) => any = (d) => {
    console.log(d);
  };

  export let records: Record[] = [];
  $: selectionStates = records.map(r => {return {data: r, selected: false}});

  let deleteIcon: string = "delete_outline";

  let innerWidth;
  let isLarge: boolean = true;

  $: if (innerWidth <= 800 && isLarge) {
    isLarge = false;
  } else if (innerWidth >= 800 && !isLarge) {
    isLarge = true;
  }
</script>

<svelte:window bind:innerWidth />

<main>
  {#if isLarge}
  <table class="pf-record-table">
    <tr class="pf-record-table__tr">
      {#if allowSelection && allowDeletion}
      <th on:click={() => {handleDeletion(selectionStates.filter(r => r.selected).map(r => r.data))}} class="pf-record-table__header material-icons" style="display: flex; font-size: 20px; cursor: pointer;">
        {deleteIcon}
      </th>
      {:else if allowSelection}
      <th class="pf-record-table__header"></th>
      {/if}
      {#each ["Label", "Type", "TTL", "Value", "", ""] as head}
        <th class="pf-record-table__header">{head}</th>
      {/each}
    </tr>
    <tr class="pf-record-table__spacer"></tr>
    {#each records as record, i}
      <tr class="pf-record-table__spacer"></tr>
      <Record {allowDeletion} {allowSelection} handleSelection={(s, d, e) => {selectionStates[i].selected = s; handleSelection(s, d, e)}} {record} zebra={i%2 === 0} />
    {/each}
  </table>
  {:else}
    <div class="pf-record-table_mobile">
      {#each records as record, i}
      <Record mobile {allowDeletion} {allowSelection} handleSelection={(s, d, e) => {selectionStates[i].selected = s; handleSelection(s, d, e)}} {record} zebra={i%2 === 0} />
      {/each}
    </div>
  {/if}
</main>

<style lang="scss" src="./RecordTable.scss" global></style>
