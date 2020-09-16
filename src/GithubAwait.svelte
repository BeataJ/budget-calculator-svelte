<script>
  const getUsers = async () => {
    let userData = await fetch('https://api.github.com/users');
    let githubUsers = await userData.json();
    return githubUsers;
  };
</script>

<h2>Hello from githubawait</h2>
