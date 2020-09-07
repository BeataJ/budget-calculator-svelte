<script>
  import SectionTitle from './Title.svelte';
  import SingleExpense from './SingleExpense.svelte';
  export let expenses = [];
</script>

<section>
  <SectionTitle title="expense list" />
  <ul>
    {#each expenses as expense}{/each}
  </ul>
</section>
