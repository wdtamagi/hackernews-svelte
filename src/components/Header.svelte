<script>
  import { link } from "svelte-routing";

  const authToken = localStorage.getItem("auth-token");
  console.log(authToken);

  const logout = () => {
    localStorage.removeItem(AUTH_TOKEN);
    history.push(`/`);
  };
</script>

<style>
  .appBar {
    display: flex;
    width: 100%;
    height: 1.5rem;
    background-color: #ff6600;
    align-items: baseline;
  }

  .mainLink {
    font-family: Verdana, Geneva, sans-serif;
    font-size: 0.9rem;
    font-weight: 700;
    color: #000;
    margin: 0 0.5rem;
  }

  .normalLink {
    font-family: Verdana, Geneva, sans-serif;
    font-size: 0.9rem;
    color: #000;
  }

  .loginGroup {
    margin-left: auto;
    margin-right: 0.5rem;
  }

  .loginLink {
    font-family: Verdana, Geneva, sans-serif;
    font-size: 0.9rem;
    color: #000;
    margin-left: auto;
    margin-right: 0.5rem;
  }

  span {
    margin: 0 0.3rem;
  }
</style>

<div class="appBar">
  <a class="mainLink" href="/" use:link>Hacker News</a>
  <a class="normalLink" href="/" use:link>new</a>
  <span>|</span>
  <a class="normalLink" href="/top" use:link>top</a>
  <span>|</span>
  <a class="normalLink" href="/search" use:link>search</a>
  <span>|</span>
  {#if authToken}
    <a class="normalLink" href="/create">submit</a>
  {/if}
  <div class="loginGroup">
    {#if authToken}
      <div class="loginLink" on:click={logout}>logout</div>
    {:else}
      <a class="loginLink" href="/login" use:link>login</a>
    {/if}
  </div>
</div>
