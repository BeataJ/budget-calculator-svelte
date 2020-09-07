<script>
  import Navbar from './Navbar.svelte';
  import Title from './Title.svelte';
  let fruits = ['apple', 'orange', 'lemon'];
</script>

<style>
</style>

<Navbar />

{#each fruits as item}
  <Title title={item} />
{/each}
