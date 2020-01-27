<script>
  import { Link } from "svelte-routing";
</script>

<style>
  div {
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

<div>
  <Link class="mainLink" to="/">Hacker News</Link>
  <Link class="normalLink" to="/">new</Link>
  <span>|</span>
  <Link class="normalLink" to="/top">top</Link>
  <span>|</span>
  <Link class="normalLink" to="/search">search</Link>
  <span>|</span>
  <Link class="loginLink" to="/login">login</Link>
</div>
