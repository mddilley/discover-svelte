<script>
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
  let address = crashDetails.address_confirmed_primary;
</script>

<Container class="text-center">
  <h1 class="mb-3">Edit Crash Details</h1>
  <Form>
    <FormGroup>
      <Label for="exampleEmail">Primary Address</Label>
      <Input type="text" name="email" id="exampleEmail" value={address} />
    </FormGroup>
  </Form>
  <Button>Submit</Button>
</Container>
