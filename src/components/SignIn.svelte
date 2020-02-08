<script>
  import { getClient, mutate } from "svelte-apollo";
  import { gql } from "apollo-boost";
  import { createEventDispatcher } from "svelte";

  const client = getClient();
  const dispatch = createEventDispatcher();

  let email = "";
  let password = "";

  const LOGIN_MUTATION = gql`
    mutation LoginMutation($email: String!, $password: String!) {
      login(email: $email, password: $password) {
        token
      }
    }
  `;
  async function signIn() {
    try {
      await mutate(client, {
        mutation: LOGIN_MUTATION,
        variables: { email, password }
      });
    } catch (error) {
      // TODO
    }
  }

  function changeContext() {
    dispatch("changeContext", {
      text: "signUp"
    });
  }
</script>

<style>
  .labels {
    width: 150px;
  }

  .inputs {
    width: 300px;
  }

  button {
    width: 150px;
  }
</style>

<div>
  <h2>Login</h2>
  <div>
    <div class="labels">Email:</div>
    <input class="inputs" type="text" bind:value={email} />
  </div>
  <div>
    <div class="labels">Password:</div>
    <input class="inputs" type="password" bind:value={password} />
  </div>
  <button on:click={signIn}>Login</button>
  <button on:click={changeContext}>Create account</button>
</div>
