<script>
  import {userSession} from '../store';
  import Cookies from 'js-cookie';
  let user;
  userSession.subscribe(val => {
    user = val
  });

  function logout() {
    userSession.update(() => null);
    Cookies.remove('token');
  }
</script>

<nav>
  <a href="/">Home</a>
  {#if user}
    <a href="/posts/new">New Post</a>
    <!-- svelte-ignore a11y-invalid-attribute -->
    <a href="#" on:click={logout}> Logout </a>
  {:else}
    <a href="/login">Login</a>
    <a href="/register">Register</a>
  {/if}
  <hr />
</nav>