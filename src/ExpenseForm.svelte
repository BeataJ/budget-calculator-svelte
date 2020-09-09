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
  </form>
</section>
