<script lang="ts">
  import type { DataHandler } from "@vincjo/datatables"
  import BaseButton from "../Base/BaseButton.svelte";

  export let handler: DataHandler

  const pageNumber = handler.getPageNumber()
  const pageCount = handler.getPageCount()
  const pages = handler.getPages({ ellipsis: true })
</script>

<section class="ml-auto flex gap-2">
  <BaseButton
    type="button"
    extraClasses={{
      'from-slate-600 via-slate-300 to-slate-600': $pageNumber === 1
    }}
    on:click={() => handler.setPage('previous')}
  >
    {@html handler.i18n.previous}
  </BaseButton>
  {#each $pages as page}
    <BaseButton
      type="button"
      extraClasses={{
        'from-red-400 via-cyan-200 to-emerald-300 shadow-xl': $pageNumber === page,
        ellipse: page === null
      }}
      on:click={() => handler.setPage(page)}
    >
      {page ?? '...'}
    </BaseButton>
  {/each}
  <BaseButton
    type="button"
    extraClasses={{
      'from-slate-600 via-slate-300 to-slate-600': $pageNumber === $pageCount
    }}
    on:click={() => handler.setPage('next')}
  >
    {@html handler.i18n.next}
  </BaseButton>
</section>

<style>

</style>
