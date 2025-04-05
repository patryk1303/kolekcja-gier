<script lang="ts">
export let type: 'button' | 'submit' | 'reset' = 'button'
export let extraClasses: Record<string, boolean> = {}
export let active: boolean = false

$: classesToUse = Object.entries(extraClasses)
  .filter(([_className, predicate]) => predicate)
  .map(([className, _predicate]) => className)
  .join(' ')

$: bgClasses = active
  ? 'bg-yellow-200 hover:bg-yellow-300 focus-visible:bg-yellow-300'
  : 'bg-blue-200 hover:bg-orange-200 focus-visible:bg-orange-200'
</script>

<button
  class="p-4 rounded-md {bgClasses} {classesToUse} shadow-xl"
  {type}
  on:click
><slot /></button>
