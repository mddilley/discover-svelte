<script>
  import CrashEdit from "./CrashEdit.svelte";
  import { gql } from "apollo-boost";
  export let id;
  const crashQuery = gql`
    query GetCrashe {
      atd_txdot_crashes(where: { crash_id: { _eq: ${id} } }) {
        crash_id
        case_id
        crash_date
        address_confirmed_primary
        sus_serious_injry_cnt
        death_cnt
      }
    }
  `;
  import { getClient, query } from "svelte-apollo";
  import { Table, Container, Spinner } from "sveltestrap";

  const client = getClient();

  const crash = query(client, { query: crashQuery });
</script>

<Container class="text-center">
  <h1 class="mb-3">Crashes</h1>
  <!-- Await block -->
  {#await $crash}
    <Spinner class="mt-5" />
    <h3 class="mt-2 pl-4">Loading...</h3>
  {:then result}
    <Table>
      <thead>
        <tr>
          <th>Crash ID</th>
          <th>Case Number</th>
          <th>Crash Date</th>
          <th>Primary Address</th>
          <th>Serious Injury Count</th>
          <th>Fatality Count</th>
        </tr>
      </thead>
      <tbody>
        {#each result.data.atd_txdot_crashes as crash}
          <tr>
            <th scope="row">{crash.crash_id || 'Not available'}</th>
            <td>{crash.case_id || 'Not available'}</td>
            <td>{crash.crash_date || 'Not available'}</td>
            <td>{crash.address_confirmed_primary || 'Not available'}</td>
            <td>{crash.sus_serious_injry_cnt}</td>
            <td>{crash.death_cnt}</td>
          </tr>
        {/each}
      </tbody>
    </Table>
    <CrashEdit {crash} crashDetails={result.data.atd_txdot_crashes[0]} />
  {:catch error}
    Error: {error}
  {/await}
</Container>
