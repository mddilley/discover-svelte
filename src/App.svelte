<script>
  export let name;
  import ApolloClient from "apollo-boost";
  import { setClient } from "svelte-apollo";
  import CrashTable from "./CrashTable.svelte";
  const ENDPOINT = "https://vzd-staging.austinmobility.io/v1/graphql";
  import { Table, Container } from "sveltestrap";
  let src = "/vz-logo.png";

  const client = new ApolloClient({
    uri: ENDPOINT,
    headers: {
      Authorization: `Bearer `,
      "x-hasura-role": "admin"
    }
  });
  setClient(client);
</script>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>

<svelte:head>
  <link
    rel="stylesheet"
    href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" />
</svelte:head>
<Container class="text-center">
  <img class="mb-4" alt="Vision Zero Logo" {src} />
  <CrashTable />
</Container>
