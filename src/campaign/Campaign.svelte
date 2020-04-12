<script>
  import { onMount } from 'svelte';
  import List, {Item, Text} from '@smui/list';
  import axios from 'axios';
  import NProgress from 'nprogress';

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
        <Item>
          <Text>{status.name}</Text>
        </Item>
      {/each}
    </List>
  {/if}
</div>