<script lang="ts">
  import type { DataHandler } from '@vincjo/datatables'
  import BaseSelect from '../Base/BaseSelect.svelte';
  export let handler: DataHandler
  export let filterBy = null
  let value = ''
</script>

<th>
  <BaseSelect
    placeholder="Platforma"
    bind:value={value}
    on:change={() => handler.filter(value, filterBy)}
  >
    <option value="">Wszystkie</option>
    <option value="PS1">PS1</option>
    <option value="PS2">PS2</option>
    <option value="PS3">PS3</option>
    <option value="PS4">PS4</option>
    <option value="PC">PC (wszystkie)</option>
    <option value="PC/Amazon">PC (Amazon)</option>
    <option value="PC/Epic">PC (Epic)</option>
    <option value="PC/GOG">PC (GOG)</option>
    <option value="PC/Steam">PC (Steam)</option>
  </BaseSelect>
</th>
