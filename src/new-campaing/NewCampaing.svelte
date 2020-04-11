<script>
  import { onMount } from 'svelte';
  import axios from 'axios';
  import Select, { Option } from '@smui/select';

  let campaings = [];
  let selectedCampaingId;
  let isLoading = true;

  onMount(async () => {
    const response = await axios.get('/campaings.json');
    campaings = response.data;
    isLoading = false;
  });

</script>

<div>
  {#if isLoading}
    Loading...
  {:else}
    <Select variant="filled" enhanced bind:value={selectedCampaingId} label="Campaing">
      <Option value=""></Option>
      {#each campaings as campaing}
        <Option value={campaing.id} selected={selectedCampaingId === campaing.id}>{ campaing.title }</Option>
      {/each}
    </Select>
    <pre class="status">Selected: {selectedCampaingId}</pre>
  {/if}
</div>

