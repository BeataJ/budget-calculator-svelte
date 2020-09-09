<script>
  import { setContext } from 'svelte';

  // Components
  import Navbar from './Navbar.svelte';
  import ExpenseList from './ExpenseList.svelte';
  // data
  import expensesData from './expenses';
  // Veriables
  let expenses = [...expensesData];
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
  <ExpenseList {expenses} />
  <button
    type="button"
    class="btn btn-primary btn-block"
    on:click={clearExpenses}>clear expenses</button>
</main>
