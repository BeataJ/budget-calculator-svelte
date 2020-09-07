<script>
  import Navbar from './Navbar.svelte';
  let fruits = ['apple', 'orange', 'lemon'];
</script>

<style>
</style>

<Navbar />

{#each fruits as item}
  <h1>Default title</h1>
{/each}
