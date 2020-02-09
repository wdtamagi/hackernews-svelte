<script>
  import { getClient, mutate } from "svelte-apollo";
  import { gql } from "apollo-boost";
  import { createEventDispatcher } from "svelte";

  const client = getClient();
  const dispatch = createEventDispatcher();

  let email = "";
  let password = "";
  let name = "";

  const SIGNUP_MUTATION = gql`
    mutation SignupMutation(
      $email: String!
      $password: String!
      $name: String!
    ) {
      signup(email: $email, password: $password, name: $name) {
        token
      }
    }
  `;
  async function signUp() {
    try {
      const result = await mutate(client, {
        mutation: SIGNUP_MUTATION,
        variables: { email, password, name }
      });
      localStorage.setItem("auth-token", result.data.signup.token);
      window.location.href = "/";
    } catch (error) {
      console.log(error);
    }
  }

  function changeContext() {
    dispatch("changeContext", {
      text: "login"
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
  <h2>Create account</h2>
  <div>
    <div class="labels">Username:</div>
    <input class="inputs" type="text" bind:value={name} />
  </div>
  <div>
    <div class="labels">Email:</div>
    <input class="inputs" type="text" bind:value={email} />
  </div>
  <div>
    <div class="labels">Password:</div>
    <input class="inputs" type="password" bind:value={password} />
  </div>
  <button on:click={signUp}>Create account</button>
  <button on:click={changeContext}>Have an Account?</button>
</div>
