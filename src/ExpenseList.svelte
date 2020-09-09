<script>
  import SectionTitle from './Title.svelte';
  import SingleExpense from './SingleExpense.svelte';
  import App from './App.svelte';
  export let expenses = [];
</script>

<style>
  h2 {
    text-transform: capitalize;
  }
</style>

<section>
  <SectionTitle title="expense list" />
  <ul>
    {#each expenses as expense}
      <SingleExpense {...expense} />
    {:else}
      <h2>currently you have no expenses</h2>
    {/each}
  </ul>
</section>
