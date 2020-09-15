<script>
  import { fade, blur, fly, slide, scale } from 'svelte/transition';
  import { getContext } from 'svelte';
  export let id;
  export let name = '';
  export let amount = 0;
  let displayAmount = false;
  const toggleAmount = () => {
    displayAmount = !displayAmount;
  };
  const removeExpense = getContext('remove');
  const setModifiedExpense = getContext('modify');
  // const dispatch = createEventDispatcher();
</script>

<article class="single-expense">
  <div class="expense-info">
    <h2>
      {name}
      <button class="amount-btn" on:click={toggleAmount}>
        <i class="fas fa-caret-down" />
      </button>
    </h2>
    {#if displayAmount}
      <h4 transition:fly={{ x: 50, y: 50, duration: 2000, delay: 300 }}>
        amount: ${amount}
      </h4>
    {/if}
  </div>
  <div class="expense-buttons">
    <button class="expense-btn edit-btn"><i
        class="fas fa-pen"
        on:click={() => setModifiedExpense(id)} /></button>
    <button class="expense-btn delete-btn" on:click={() => removeExpense(id)}><i
        class="fas fa-trash" /></button>
  </div>
</article>
