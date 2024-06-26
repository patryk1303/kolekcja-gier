<script lang="ts">
import type { DataHandler } from '@vincjo/datatables'
import BaseInput from '../Base/BaseInput.svelte'
export let handler: DataHandler
export let filterBy = null
let value = ''
</script>

<th>
  <BaseInput
    placeholder="Filtruj"
    bind:value
    on:input={() => handler.filter(value, filterBy)}
  />
</th>
