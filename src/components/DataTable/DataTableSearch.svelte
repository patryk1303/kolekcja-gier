<script lang="ts">
import BaseInput from '../Base/BaseInput.svelte'
import type { DataHandler } from '@vincjo/datatables'
export let handler: DataHandler
let value = ''
</script>

<BaseInput
  placeholder={handler.i18n.search}
  bind:value
  on:input={() => handler.search(value)}
/>
