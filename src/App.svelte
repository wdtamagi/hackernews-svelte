<script>
  import { Router, Route } from "svelte-routing";
  import ApolloClient from "apollo-boost";
  import { setClient } from "svelte-apollo";
  import Header from "./features/header/Header.svelte";
  import LinkList from "./components/LinkList.svelte";
  import Login from "./features/login/Login.svelte";

  const client = new ApolloClient({ uri: "http://localhost:4000" });
  setClient(client);
  export let url = "";
</script>

<style>
  div {
    width: 85%;
    margin: 0 auto;
  }
</style>

<div>
  <Router {url}>
    <Header />
    <Route path="/" component={LinkList} />
    <Route path="new/:page" component={LinkList} />
    <Route path="top" component={LinkList} />
    <Route path="search" component={LinkList} />
    <Route path="login" component={Login} />
    <Route path="create" component={LinkList} />
  </Router>
</div>
