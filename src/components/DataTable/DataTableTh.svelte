<script lang="ts">
  import type { DataHandler } from '@vincjo/datatables'
  export let handler: DataHandler
  export let orderBy = null

  const identifier = orderBy?.toString()
  const sorted = handler.getSort()
</script>

<th
  on:click={() => handler.sort(orderBy)}
  class="p-2 cursor-pointer bg-gradient-to-t from-yellow-200 to-lime-200 group"
  class:active={$sorted.identifier === identifier}
>
  <div class="p-0 flex justify-start items-center h-full">
      <strong>
          <slot />
      </strong>
      {#if $sorted.direction}
        <span class="hidden group-[.active]:block">{$sorted.direction === 'asc' ? '🔼' : '🔽'}</span>
      {/if}
  </div>
</th>

<style lang="postcss">
  th.active {
    @apply underline underline-offset-4;
  }
</style>
