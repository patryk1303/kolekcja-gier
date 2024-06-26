<script lang="ts">
import type { DataHandler } from '@vincjo/datatables'
export let handler: DataHandler
const rowCount = handler.getRowCount()
</script>

<aside class="text-xl text-slate-900">
  {#if $rowCount.total > 0}
    {@html handler.i18n.rowCount
      .replace('{start}', `<b>${$rowCount.start}</b>`)
      .replace('{end}', `<b>${$rowCount.end}</b>`)
      .replace('{total}', `<b>${$rowCount.total}</b>`)}
  {:else}
      {handler.i18n.noRows}
  {/if}
</aside>
