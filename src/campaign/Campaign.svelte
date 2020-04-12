<script>
  import { onMount } from 'svelte';
  import axios from 'axios';
  import NProgress from 'nprogress';

  export let capmaignId = 0;

  let campaignState = [];
  let isLoading = true;

  onMount(async () => {
    NProgress.start();
    const response = await axios.get(`/statuses/${capmaignId}.json`);
    campaignState = response.data;
    isLoading = false;
    NProgress.done();
  });

</script>

<div>
  { JSON.stringify(campaignState) }
</div>