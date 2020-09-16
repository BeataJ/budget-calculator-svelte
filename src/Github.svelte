<script>
  import { onMount } from 'svelte';
  let users = [];
  let loading = true;
</script>

<style>
  h2 {
    text-align: center;
  }
</style>

{#if loading}
  <h2>Loading...</h2>
{:else}
  <h2>Data</h2>
{/if}
