<script>
  import ApolloClient from "apollo-boost";
  import { Router, Route } from "svelte-routing";
  import { setClient } from "svelte-apollo";
  import CrashTable from "./CrashTable.svelte";
  import Crash from "./Crash.svelte";
  import { Table, Container } from "sveltestrap";

  const ENDPOINT = "https://vzd-staging.austinmobility.io/v1/graphql";
  export let url = "";

  const client = new ApolloClient({
    uri: ENDPOINT,
    headers: {
      Authorization: `Bearer `,
      "x-hasura-role": "admin"
    }
  });
  setClient(client);
</script>

<svelte:head>
  <link
    rel="stylesheet"
    href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" />
</svelte:head>

<Router {url}>
  <!-- <nav>
    <Link to="/">Home</Link>
    <Link to="about">About</Link>
    <Link to="blog">Blog</Link>
  </nav> -->
  <div>
    <Route path="crash/:id" component={Crash} />
    <Route path="/">
      <CrashTable />
    </Route>
  </div>
</Router>
