<script>
  import SectionTitle from './Title.svelte';
  import SingleExpense from './SingleExpense.svelte';
  import { fly } from 'svelte/transition';
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
    {#each expenses as expense, index}
      <div transition:fly={{ x: 200, delay: index * 700 }}>
        <SingleExpense {...expense} />
      </div>
    {:else}
      <h2>no expenses added to the list</h2>
    {/each}
  </ul>
</section>
