<script>
  import { onMount } from 'svelte';
  import List from '@smui/list';
  import axios from 'axios';
  import NProgress from 'nprogress';
  import StatusListItem from './StatusListItem.svelte';

  export let capmaignId = 0;

  const userId = 'aaa';

  let campaignStatuses = [];
  let isLoading = true;

  onMount(async () => {
    NProgress.start();
    const response = await axios.get(`/statuses/${capmaignId}.json`);
    campaignStatuses = response.data;
    isLoading = false;
    NProgress.done();
  });

  function updateStatus(changeObject) {
    console.warn('status changed: ', changeObject);
    // TODO: Save status changes here
    // use PUT request to create new intro with pre-defined key for Firebase
  }

</script>

<div>
  {#if isLoading}
    Loading...
  {:else}
    <List nonInteractive>
      {#each campaignStatuses as status}
        <StatusListItem statusItem={status} on:statusChange={updateStatus}></StatusListItem>
      {/each}
    </List>
  {/if}
</div>
