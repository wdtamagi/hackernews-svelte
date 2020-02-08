<script>
  import SignIn from "../../components/SignIn.svelte";
  import SignUp from "../../components/SignUp.svelte";

  let loginContext = "login";

  const changeContext = event => (loginContext = event.detail.text);
</script>

<style>

</style>

<div>
  {#if loginContext === 'login'}
    <SignIn on:changeContext={changeContext} />
  {:else}
    <SignUp on:changeContext={changeContext} />
  {/if}
</div>
