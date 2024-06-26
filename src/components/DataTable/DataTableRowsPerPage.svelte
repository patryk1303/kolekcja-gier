<script lang="ts">
import BaseSelect from '../Base/BaseSelect.svelte'
import type { DataHandler } from '@vincjo/datatables'
export let handler: DataHandler
const rowsPerPage = handler.getRowsPerPage()
const options = [5, 10, 20, 50, 100]
</script>

<aside class="flex gap-2 items-center justify-end ml-auto">
  {handler.i18n.show}
  <BaseSelect bind:value={$rowsPerPage}>
    {#each options as option}
      <option value={option}>
        {option}
      </option>
    {/each}
  </BaseSelect>
  {handler.i18n.entries}
</aside>
