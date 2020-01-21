<script>
  import ApolloClient from "apollo-boost";
  import { setClient } from "svelte-apollo";
  import Header from "./Header.svelte";
  import LinkList from "./LinkList.svelte";

  const client = new ApolloClient({ uri: "http://localhost:4000" });
  setClient(client);
</script>

<style>
  div {
    width: 85%;
    margin: 0 auto;
  }
</style>

<div>
  <Header />
  <LinkList />
</div>
