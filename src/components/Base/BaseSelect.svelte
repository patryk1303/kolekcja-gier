<script lang="ts">
export let placeholder: string = ''
export let value: string | number = ''
</script>

  <th>
    <select
      class="p-2 min-w-16 text-xs w-full rounded bg-lime-100 border-none"
      {placeholder}
      bind:value
      on:change
    >
      <slot />
    </select>
  </th>
