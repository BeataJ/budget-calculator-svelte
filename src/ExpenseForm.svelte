<script>
  import App from './App.svelte';
  import Title from './Title.svelte';
</script>

<section class="form">
  <Title title="add expense" />
  <form class="expense-form">
    <div class="form-control">
      <label for="name">name</label>
      <input type="text" id="name" />
    </div>
    <div class="form-control">
      <label for="amount">amount</label>
      <input type="number" id="amount" />
    </div>
    <p class="form-empty">please fill out all form fields</p>
  </form>
</section>
