<script>
  import { onMount } from 'svelte';
  import List from '@smui/list';
  import axios from 'axios';
  import NProgress from 'nprogress';
  import StatusListItem from './StatusListItem.svelte';

  export let capmaignId = 0;

  let campaignStatuses = [];
  let isLoading = true;

  onMount(async () => {
    NProgress.start();
    const response = await axios.get(`/statuses/${capmaignId}.json`);
    campaignStatuses = response.data;
    isLoading = false;
    NProgress.done();
  });

</script>

<div>
  {#if isLoading}
    Loading...
  {:else}
    <List nonInteractive>
      {#each campaignStatuses as status}
        <StatusListItem statusItem={status}></StatusListItem>
      {/each}
    </List>
  {/if}
</div>
