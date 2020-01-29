<script>
  export let router = {};
</script>

<style>
  .labels {
    width: 150px;
  }

  .inputs {
    width: 300px;
  }

  .button {
    width: 150px;
  }
</style>

<div>
  <h2>Login</h2>
  <div>
    <div class="labels">Username:</div>
    <input class="inputs" type="text" />
  </div>
  <div>
    <div class="labels">Password:</div>
    <input class="inputs" type="password" />
  </div>
  <button class="button">Login</button>

  <h2>Create account</h2>
  <div>
    <div class="labels">Username:</div>
    <input class="inputs" type="text" />
  </div>
  <div>
    <div class="labels">Password:</div>
    <input class="inputs" type="password" />
  </div>
  <button class="button">Create account</button>
</div>
