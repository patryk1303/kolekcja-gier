<script lang="ts">
export let type: 'button' | 'submit' | 'reset' = 'button'
export let extraClasses: Record<string, boolean> = {}

$: classesToUse = Object.entries(extraClasses)
  .filter(([_className, predicate]) => predicate)
  .map(([className, _predicate]) => className)
  .join(' ')
</script>

<button
  class="p-4 rounded-md bg-gradient-to-bl from-emerald-100 via-cyan-100 to-red-100 {classesToUse} shadow-xl"
  {type}
  on:click
><slot /></button>
