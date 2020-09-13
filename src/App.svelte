<script>
  import { setContext } from 'svelte';

  // Components
  import Navbar from './Navbar.svelte';
  import ExpenseList from './ExpenseList.svelte';
  // data
  import expensesData from './expenses';
  import Totals from './Totals.svelte';
  import ExpenseForm from './ExpenseForm.svelte';
  // Veriables
  let expenses = [...expensesData];
  // set editing variables
  let setName = '';
  let setAmount = null;
  let setId = null;
  // reactive
  $: isEditing = setId ? true : false;
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
  const addExpense = ({ name, amount }) => {
    let expense = { id: Math.random() * Date.now(), name, amount };
    expenses = [expense, ...expenses];
  };
  const setModifiedExpense = (id) => {
    let expense = expenses.find((item) => item.id === id);
    setId = expense.id;
    setName = expense.name;
    setAmount = expense.amount;
  };
  const editExpense = ({ name, amount }) => {
    expenses = expenses.map((item) => {
      return item.id === setId ? { ...item, name, amount } : { ...item };
    });
    setId = null;
    setName = '';
    setAmount = null;
  };
  // context
  setContext('remove', removeExpense);
  setContext('modify', setModifiedExpense);
  $: console.log({ setName, setAmount });
</script>

<Navbar />
<main class="content">
  <ExpenseForm
    bind:name={setName}
    bind:amount={setAmount}
    {isEditing}
    <!-- {addExpense}
    {editExpense}  -->
    />
  <Totals title="total expenses" {total} />
  <ExpenseList {expenses} />
  <button
    type="button"
    class="btn btn-primary btn-block"
    on:click={clearExpenses}>clear expenses</button>
</main>
