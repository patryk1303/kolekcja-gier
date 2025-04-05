<script lang="ts">
import { DataHandler, Search } from '@vincjo/datatables'

import DataTableTh from './DataTableTh.svelte'
import DataTableThFilter from './DataTableThFilter.svelte'
import DataTableThFilterMedium from './DataTableThFilterMedium.svelte'
import DataTableThFilterPlatform from './DataTableThFilterPlatform.svelte'
import DataTableSearch from './DataTableSearch.svelte';
import DataTableRowsPerPage from './DataTableRowsPerPage.svelte';
import DataTableRowCount from './DataTableRowCount.svelte';
import DataTablePagination from './DataTablePagination.svelte';

import type { TGameRow } from '../../@types/TGame'

export let data: TGameRow[] = []

const handler = new DataHandler(data, {
  rowsPerPage: 50,
  i18n: {
      search: 'Wyszukaj...',
      show: 'Pokaż',
      entries: 'gier',
      filter: 'Filtry',
      rowCount: 'Gry od {start} do {end} z {total}',
      noRows: 'Brak gier',
      previous: '⬅️',
      next: '➡️'
  }
});
const rows = handler.getRows()
</script>

<header class="flex gap-4 mb-8 pb-4 border-b-2 border-b-lime-800">
  <DataTableSearch {handler} />
  <DataTableRowsPerPage {handler} />
</header>

<table class="table w-full border-collapse">
  <thead>
    <tr class="border-b border-slate-700">
      <DataTableTh {handler} orderBy="number">Lp.</DataTableTh>
      <DataTableTh {handler} orderBy="title">Nazwa Gry</DataTableTh>
      <DataTableTh {handler} orderBy="media">Medium</DataTableTh>
      <DataTableTh {handler} orderBy="platform">Platforma</DataTableTh>
      <DataTableTh {handler} orderBy="status">Stan</DataTableTh>
      <DataTableTh {handler} orderBy="notes">Uwagi</DataTableTh>
    </tr>
    <tr>
      <th></th>
      <DataTableThFilter {handler} filterBy="title" />
      <DataTableThFilterMedium {handler} filterBy="media" />
      <DataTableThFilterPlatform {handler} filterBy="platform" />
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    {#each $rows as row, rowIdx}
      <tr
        style="--tw-bg-opacity: 0.5"
        class="hover:bg-red-50"
        class:bg-yellow-50={rowIdx % 2 === 0}
      >
        <td class="p-2">{row.number}</td>
        <td class="p-2">{row.title}</td>
        <td class="p-2">{row.media}</td>
        <td class="p-2">{row.platform}</td>
        <td class="p-2">{row.status}</td>
        <td class="p-2">{row.notes}</td>
      </tr>
    {/each}
  </tbody>
</table>

<footer class="flex gap-4 mt-8 pt-4 border-t-2 border-t-lime-800">
  <DataTableRowCount {handler} />
  <DataTablePagination {handler} />
</footer>
