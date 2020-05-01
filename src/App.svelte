<script>
  export let name;
  import ApolloClient from "apollo-boost";
  import { setClient } from "svelte-apollo";
  import Form from "./Form.svelte";
  import CrashTable from "./CrashTable.svelte";
  const ENDPOINT = "https://vzd-staging.austinmobility.io/v1/graphql";

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

<main>
  <h1>Hello {name}!</h1>
  <p>
    Visit the
    <a href="https://svelte.dev/tutorial">Svelte tutorial</a>
    to learn how to build Svelte apps.
  </p>
</main>
<CrashTable />
<Form />
