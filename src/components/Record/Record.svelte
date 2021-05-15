<script lang="ts">
  type Record = {
    label: string;
    type: string;
    ttl: number;
    value: string;
  };
  export let record: Record;
  export let zebra: boolean = false;

  let open: boolean = false;

  const handleDropdown = () => {
    open = !open;
  }
</script>

<tr class="pf-record" class:zebra>
  <td class="pf-record__label">{record.label}</td>
  <td class="pf-record__type">{record.type}</td>
  <td class="pf-record__ttl">{record.ttl}</td>
  <td class="pf-record__value">{record.value}</td>
  <td on:click={handleDropdown} class="pf-record__arrow"
    ><span class="material-icons-round"> arrow_forward </span></td
  >
</tr>
<span class="pf-record__dropdown" class:open style="--h:{open ? 200 : 0}px;"></span>

<style lang="scss" src="./Record.scss" global>
</style>
