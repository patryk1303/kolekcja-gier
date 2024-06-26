<script lang="ts">

export let value = ''
export let placeholder: string
</script>

<input
  type="text"
  {placeholder}
  bind:value
  on:input
  class="p-2 text-xs w-full rounded bg-lime-100 border-none"
/>
