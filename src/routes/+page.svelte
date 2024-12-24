<script lang="ts">
  type TestObject = {
    propA: string
    propB: string
    propC: string
  }

  let items: TestObject[] = []

  for (const { propA, ...restProps } of items) {
    console.log(propA, restProps)
  }
</script>

{#each items as { propA, propB, propC }}
  {propA} {propB} {propC}
{/each}

<!--
The code below appears to be correct for version 109.3.3 and earlier.

In version 109.4.0, many errors (ts2352, ts7008, ts1131, ts2556, ts2304, ts1005, ts1128) are displayed.

This code is correct because svelte-check determines it to be correct.
-->
{#each items as { propA, ...restProps }}
  {propA} {restProps}
{/each}
