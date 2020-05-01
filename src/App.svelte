<script>
  import ApolloClient from "apollo-boost";
  import { setClient } from "svelte-apollo";
  import CrashTable from "./CrashTable.svelte";
  import { Table, Container } from "sveltestrap";

  const ENDPOINT = "https://vzd-staging.austinmobility.io/v1/graphql";
  let src = "/vz-logo.png";

  const client = new ApolloClient({
    uri: ENDPOINT,
    headers: {
      Authorization: `Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCIsImtpZCI6Ik5EVkZNa0ZFTlRJeFEwUTRNMFpCTVRORU56azBNakpFUmpnMVF6WTFPVFZFUXpKR09UVkVOUSJ9.eyJodHRwczovL2hhc3VyYS5pby9qd3QvY2xhaW1zIjp7IngtaGFzdXJhLWRlZmF1bHQtcm9sZSI6InJlYWRvbmx5IiwieC1oYXN1cmEtYWxsb3dlZC1yb2xlcyI6WyJpdFN1cGVydmlzb3IiLCJhZG1pbiJdLCJ4LWhhc3VyYS11c2VyLWlkIjoiYXV0aDB8NWQ1NzA4ZGQ3MTkwZDIwY2FlOTU0YmQ0In0sIm5pY2tuYW1lIjoibWlrZS5kaWxsZXkiLCJuYW1lIjoibWlrZS5kaWxsZXlAYXVzdGludGV4YXMuZ292IiwicGljdHVyZSI6Imh0dHBzOi8vcy5ncmF2YXRhci5jb20vYXZhdGFyLzVlMDAwMGQ5YjhkMTMyN2UwODA5NzdkOWMwZmYzYjI1P3M9NDgwJnI9cGcmZD1odHRwcyUzQSUyRiUyRmNkbi5hdXRoMC5jb20lMkZhdmF0YXJzJTJGbWkucG5nIiwidXBkYXRlZF9hdCI6IjIwMjAtMDUtMDFUMTk6Mjc6MTYuNDcyWiIsImVtYWlsIjoibWlrZS5kaWxsZXlAYXVzdGludGV4YXMuZ292IiwiZW1haWxfdmVyaWZpZWQiOnRydWUsImlzcyI6Imh0dHBzOi8vYXRkLWRhdGF0ZWNoLmF1dGgwLmNvbS8iLCJzdWIiOiJhdXRoMHw1ZDU3MDhkZDcxOTBkMjBjYWU5NTRiZDQiLCJhdWQiOiIycWJxejJzZjhMOWlkQk93bjBkNVlBOWVmTmdRYkw3YyIsImlhdCI6MTU4ODM2MTIzOCwiZXhwIjoxNTg4Mzk3MjM4LCJub25jZSI6IjlpS1Zkd2lJUE1Xc2pCM3FZUXpTNTBOTGMzRTNXZTlfUmp5aEQ4QW5rSnUifQ.ChiT-b4nU0POR1pKmSzhi_RS89yJzS8F8ciElTQW_r3tAkEjMkwdCgeY2-VD61P9-e4GJioa0hHRGwQ6sOjTY-uxpehgMwao72QzS_lT5y4CNgXzY5BD6XznEXTzGBjdR9rviaLqQsrG9DuNgozPHSum7ok1m7cw0pqX1tCRSP6Klx_veVa559Za9dK5DgeHl6r0zchN9bozUbIyaGF07XJYrsfpBrs3ckYMQ6dSRzbPjQmMsk85DMRU5iKUP7uNeW3pynWfMqProBXJiUeZVQ4mDB_4vxY1xpHu1_Z0AWJFWJ46Gb5f-qYSuLjRoWlj1ATFTmyYu4mtwGpXDvVqiA`,
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

<Container class="text-center">
  <img class="mb-4" alt="Vision Zero Logo" {src} />
  <CrashTable />
</Container>
