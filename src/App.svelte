<script>
  // import Github from './Github.svelte';
  // import GithubAwait from './GithubAwait.svelte';
  import { setContext, onMount, afterUpdate } from 'svelte';

  // Components
  import Navbar from './Navbar.svelte';
  import ExpenseList from './ExpenseList.svelte';
  import Totals from './Totals.svelte';
  import ExpenseForm from './ExpenseForm.svelte';
  import Modal from './Modal.svelte';
  // data
  // import expensesData from './expenses';
  // Veriables
  let expenses = [];
  // set editing variables
  let setName = '';
  let setAmount = null;
  let setId = null;
  // toggle form veriables
  let isFormOpen = false;
  // reactive
  $: isEditing = setId ? true : false;
  $: total = expenses.reduce((acc, curr) => {
    return (acc += curr.amount);
  }, 0);
  // functions
  const showForm = () => {
    isFormOpen = true;
  };
  const hideForm = () => {
    isFormOpen = false;
    setName = '';
    setAmount = null;
    setId = null;
  };
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
    showForm();
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
  // local storege
  const setLocalStorage = () => {
    localStorage.setItem('expenses', JSON.stringify(expenses));
  };
  onMount(() => {
    expenses = localStorage.getItem('expenses')
      ? JSON.parse(localStorage.getItem('expenses'))
      : [];
  });
  afterUpdate(() => {
    console.log('after update');
    setLocalStorage();
  });
</script>

<Navbar {showForm} />
<main class="content">
  <!-- <GithubAwait /> -->
  {#if isFormOpen}
    <Modal>
      <ExpenseForm
        {addExpense}
        name={setName}
        amount={setAmount}
        {isEditing}
        {editExpense}
        {hideForm} />
    </Modal>
  {/if}

  <Totals title="total expenses" {total} />
  <ExpenseList {expenses} />
  <button
    type="button"
    class="btn btn-primary btn-block"
    on:click={clearExpenses}>clear expenses</button>
</main>
