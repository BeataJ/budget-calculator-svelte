<script>
  const getUsers = async () => {
    let userData = await fetch('https://api.github.com/users');
    let githubUsers = await userData.json();
    return githubUsers;
  };
</script>

<section>
  {#await getUsers()}
    <h2>...loading</h2>
  {:then users}
    {#each users as user}
      <article class="user">
        <img src={user.avatar_url} alt={user.login} />
        <div class="user-info">
          <h3>User: {user.login}</h3>
          <a href={user.html_url} class="btn-primary" target="_blank">github url</a>
        </div>
      </article>
    {/each}
  {:catch error}
    <p>Something went wrong: {error.message}</p>
  {/await}
</section>
