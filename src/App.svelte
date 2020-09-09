<script>
  import { setContext } from 'svelte';

  // Components
  import Navbar from './Navbar.svelte';
  import ExpenseList from './ExpenseList.svelte';
  // data
  import expensesData from './expenses';
  import Totals from './Totals.svelte';
  // Veriables
  let expenses = [...expensesData];
  // reactive
  $: total = expenses.reduce((acc, curr) => {
    return (acc += curr.amount);
  }, 0);
  // functions
  const removeExpense = (id) => {
    expenses = expenses.filter((item) => item.id !== id);
  };

  const clearExpenses = () => {
    expenses = [];
  };

  // const state = {
  //   name: 'simple name',
  //   removeExpense: removeExpense,
  // };
  // context
  setContext('remove', removeExpense);
  // const deleteExpense = (e) => {
  //   const { id, name } = e.detail;
  //   console.log(name);
  //   removeExpense(id);
  // };
</script>

<Navbar />
<main class="content">
  <Totals title="total expenses" {total} />
  <ExpenseList {expenses} />

  <button
    type="button"
    class="btn btn-primary btn-block"
    on:click={clearExpenses}>clear expenses</button>
</main>
