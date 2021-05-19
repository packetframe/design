<script lang="ts">
  import Record from "../Record";

  type Record = {
    label: string,
    type: string,
    ttl: number,
    value: string,
    proxied: boolean,
  }

  export let records: Record[] = [];
</script>

<style lang="scss" src="./RecordTable.scss" global></style>

<table class="pf-record-table">
  <tr class="pf-record-table__tr">
    {#each ["Label", "Type", "TTL", "Value", "", ""] as head}
    <th class="pf-record-table__header">{head}</th>
    {/each}
  </tr>
  <tr class="pf-record-table__spacer"></tr>
  {#each records as record, i}
  <tr class="pf-record-table__spacer"></tr>
  <Record {record} zebra={i%2 === 0} />
  {/each}
</table>
