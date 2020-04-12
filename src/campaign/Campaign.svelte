<script>
  import { onMount } from 'svelte';
  import List, {Item, Text} from '@smui/list';
  import Checkbox from '@smui/checkbox';
  import FormField from '@smui/form-field';
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
          {#each Array(status.parts) as _, i}
            <FormField align="end">
              <Checkbox />
              <span slot="label">{ i + 1 }</span>
            </FormField>
          {/each}
        </Item>
      {/each}
    </List>
  {/if}
</div>
