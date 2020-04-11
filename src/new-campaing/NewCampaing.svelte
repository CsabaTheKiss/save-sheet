<script>
  import { onMount } from 'svelte';
  import axios from 'axios';

  let campaings = [];

  onMount(async () => {
    const response = await axios.get('/travelers/0.json');
    console.warn(response.data);
  });

</script>

<div>
  Start a new campaign
</div>

