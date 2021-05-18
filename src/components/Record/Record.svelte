<script lang="ts">
  import RecordField from "../RecordField";

  type Record = {
    label: string;
    type: string;
    ttl: number;
    value: string;
  };
  export let record: Record;
  export let zebra: boolean = false;

  let open: boolean = false;
</script>

<tr class="pf-record" class:zebra class:open on:click={() => open = !open}>
  <td class="pf-record__label">{record.label}</td>
  <td id="col2" class="pf-record__type">{record.type}</td>
  <td class="pf-record__ttl">{record.ttl}</td>
  <td class="pf-record__value">{record.value}</td>
  <td class="pf-record__arrow">
    <span class="material-icons-round">expand_more</span>
  </td>
</tr>
<tr class="pf-record__dropdown" class:open>
  <td colspan="5" headers="col2" class="pf-record__dropdown-wrap">
    <div class="pf-record__dropdown-anchor">
      <RecordField />
    </div>
  </td>
</tr>

<style lang="scss" src="./Record.scss" global>
</style>
