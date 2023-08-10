<script lang="ts">
  const data = {
    abuse_email: 'abusecomplaints@markmonitor.com',
 abuse_phone: '+1.2086851750',
 admin_address: 'CA, US',
 admin_email: 'REDACTED FOR PRIVACY',
 admin_fax: 'REDACTED FOR PRIVACY',
 admin_name: 'REDACTED FOR PRIVACY',
 admin_organization: 'REDACTED FOR PRIVACY',
 admin_phone: 'REDACTED FOR PRIVACY',
 billing_address: null,
 billing_email: null,
 billing_fax: null,
 billing_name: null,
 billing_organization: null,
 billing_phone: null,
 created_date: new Date('2019-09-09T15:39:04Z'),
 domain_name: 'google.com',
 expires_date: new Date('2019-09-09T15:39:04Z'),
 nameservers: ['ns1.google.com',
               'ns2.google.com',
               'ns3.google.com',
               'ns4.google.com'],
 registrant_address: 'CA, US',
 registrant_email: 'REDACTED FOR PRIVACY',
 registrant_fax: 'REDACTED FOR PRIVACY',
 registrant_name: 'REDACTED FOR PRIVACY',
 registrant_organization: null,
 registrant_phone: 'REDACTED FOR PRIVACY',
 registrar_address: '3540 E Longwing Ln, Meridian, ID, 83646, US',
 registrar_email: null,
 registrar_fax: null,
 registrar_name: null,
 registrar_phone: null,
 status: ['client update prohibited',
          'client transfer prohibited',
          'client delete prohibited',
          'server update prohibited',
          'server transfer prohibited',
          'server delete prohibited'],
 technical_address: 'CA, US',
 technical_email: 'REDACTED FOR PRIVACY',
 technical_fax: 'REDACTED FOR PRIVACY',
 technical_name: 'REDACTED FOR PRIVACY',
 technical_organization: 'REDACTED FOR PRIVACY',
 technical_phone: 'REDACTED FOR PRIVACY',
 updated_date: new Date('2019-09-09T15:39:04Z'),
label: "safe"}

 let showTable = false;

  function handleSearch(event) {
    if (event.key === 'Enter') {
      showTable = true;
    }
  }
</script>

<style>
  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
    /* 少し上にシフト */
    margin-top: 1em;
    overflow-y: auto;

  }

  .search-bar {
    margin-top: 20px;
    width: 600px;
    height: 60px;
    padding: 5px;
    font-size: 16px;
  }

  img {
    max-width: 600px;
    height: auto;
  }

  table {
    margin-top: 20px;
    /*width: 100%;
    border-collapse: collapse;*/
  }

  th, td {
    border: 1px solid black;
    padding: 8px;
    text-align: left;
  }

  .safety-message {
    font-size: 24px; /* 大きめの文字サイズ */
    margin-top: 20px;
  }

  .safety-message.safe {
    color: green;
  }

  .safety-message.danger {
    color: red;
  }
</style>


<div class="container">
  <img src="src/assets/fakenews.png" alt="Fake News Logo">
  <input class="search-bar" type="text" placeholder="検索..."　on:keydown={handleSearch}>

  {#if showTable}
  <table>
    <tbody>
      {#each Object.entries(data) as [key, value]}
        <tr>
          <td>{key}</td>
          <td>
            {#if Array.isArray(value)}
              {value[0]}
            {:else}
              {value}
            {/if}
          </td>
        </tr>
      {/each}
    </tbody>
  </table>
  {#if data.label === 'safe'}
      <p class="safety-message safe">検索したサイトは安全です</p>
    {:else}
      <p class="safety-message danger">危険です</p>
    {/if}
  {/if}
</div>