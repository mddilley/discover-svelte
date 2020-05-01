<script>
  import { gql } from "apollo-boost";
  const crashQuery = gql`
    query GetCrashes {
      atd_txdot_crashes(limit: 100, where: { city_id: { _eq: 22 } }) {
        crash_id
      }
    }
  `;
  import { getClient, query } from "svelte-apollo";

  const client = getClient();

  const crashes = query(client, { query: crashQuery });
</script>

<h1>Crash Table Test</h1>
{#await $crashes}
  Loading...
{:then result}
  {#each result.data.atd_txdot_crashes as crash}
    {crash.crash_id}
    <br />
  {/each}
{:catch error}
  Error: {error}
{/await}
