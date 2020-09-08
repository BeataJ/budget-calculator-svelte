<script>
  // Components
  import Navbar from './Navbar.svelte';
  import ExpenseList from './ExpenseList.svelte';
  // data
  import expensesData from './expenses';
  // Veriables
  let expenses = [...expensesData];
  // functions
</script>

<Navbar />
<main class="content">
  <ExpenseList {expenses} />
</main>
