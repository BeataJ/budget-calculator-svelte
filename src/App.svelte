<script>
  import { setContext } from 'svelte';
  const state = {
    name: 'simple name',
    remove: removeExpense,
  };
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
  // context
  setContext('state', state);
</script>

<Navbar />
<main class="content">
  <ExpenseList {expenses} />
</main>
