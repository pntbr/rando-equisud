<script>
  import { getTrecks } from "../stores";
  import Treck from "$lib/Treck.svelte";

  let trecks = getTrecks();
  const year = new Date().getFullYear();
</script>

<svelte:head>
  <title>Equisud riding {year}</title>
</svelte:head>
<a href="/">home</a>
<h1>Equisud riding {year}</h1>

<h2>Future trecks</h2>
<section class="weeks">
  {#each $trecks as treck}
    {#if !treck.old}
      <Treck {treck} />
    {/if}
  {/each}
</section>
<h2>Past trecks</h2>
<section class="past-treck">
  {#each $trecks as treck}
    {#if treck.old}
      <Treck {treck} />
    {/if}
  {/each}
</section>
