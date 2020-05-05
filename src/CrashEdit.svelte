<script>
  import { gql } from "apollo-boost";
  export let id;
  const crashMutation = gql`
    mutation update_atd_txdot_crashes($crashId: Int, $address: String) {
      update_atd_txdot_crashes(
        where: { crash_id: { _eq: $crashId } }
        _set: { address_confirmed_primary: $address }
      ) {
        affected_rows
      }
    }
  `;
  import { getClient, mutate } from "svelte-apollo";
  import {
    Container,
    Form,
    FormGroup,
    Label,
    Input,
    Button
  } from "sveltestrap";

  const client = getClient();

  export let crashDetails;
  let crashAddress = crashDetails.address_confirmed_primary;

  async function updateCrash() {
    try {
      await mutate(client, {
        mutation: crashMutation,
        variables: { crashId: id, address: crashAddress }
      });
    } catch (error) {
      // TODO
    }
  }
</script>

<Container class="text-center">
  <h1 class="mb-3">Edit Crash Details</h1>
  <Form>
    <FormGroup>
      <Label for="exampleEmail">Primary Address</Label>
      <Input
        type="text"
        name="email"
        id="exampleEmail"
        bind:value={crashAddress} />
    </FormGroup>
  </Form>
  <Button on:click={updateCrash}>Submit</Button>
</Container>
