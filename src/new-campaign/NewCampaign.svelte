<script>
  import { onMount } from 'svelte';
  import { navigate } from 'svelte-routing';
  import axios from 'axios';
  import Select, { Option } from '@smui/select';
  import Button, { Label } from '@smui/button';
  import NProgress from 'nprogress';

  let campaigns = [];
  let selectedCampaignId;
  let isLoading = true;

  onMount(async () => {
    NProgress.start();
    const response = await axios.get('/campaigns.json');
    campaigns = response.data;
    selectedCampaignId = campaigns[0].id;
    isLoading = false;
    NProgress.done();
  });

</script>

<div>
  {#if isLoading}
    Loading...
  {:else}
    <p class="mdc-typography--body1">Please select a campaign to start a new game.</p>
    <Select variant="filled" enhanced bind:value={selectedCampaignId} label="Campaign">
      {#each campaigns as campaign}
        <Option value={campaign.id} selected={selectedCampaignId === campaign.id}>{ campaign.title }</Option>
      {/each}
    </Select>
    <Button on:click={() => navigate(`/campaign/${selectedCampaignId}`)}>
      <Label>Start New Campaign</Label>
    </Button>
  {/if}
</div>

