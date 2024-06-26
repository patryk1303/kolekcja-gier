<script lang="ts">
import BaseSelect from '../Base/BaseSelect.svelte'
import type { DataHandler } from '@vincjo/datatables'
export let handler: DataHandler
export let filterBy = null
let value = ''
</script>

<th>
  <BaseSelect
    placeholder="Medium"
    bind:value
    on:change={() => handler.filter(value, filterBy)}
  >
    <option value="">Wszystkie</option>
    <option value="C">Cyfrowe</option>
    <option value="F">Fizyczne</option>
  </BaseSelect>
</th>
