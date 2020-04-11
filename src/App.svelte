<script>
  import Select, {Option} from '@smui/select';
  import { Route, Router } from 'svelte-routing';
  import NewCampaing from './new-campaing/NewCampaing.svelte';

  let fruits = ['Apple', 'Orange', 'Banana', 'Mango'];
  let valueFilledEnhanced = '';

  export let url = '';
</script>

<Router { url }>
  <main>
    <h1>Save Sheet</h1>
    <Route path="/new-campaing">
      <NewCampaing />
    </Route>
    <Route path="/">
      <p>Welcome to Save Sheet! Start a new campaign, or login to load an existing one.</p>
      <Select variant="filled" enhanced bind:value={valueFilledEnhanced} label="Enhanced" class="demo-select-width" menu$class="demo-select-width">
        <Option value=""></Option>
        {#each fruits as fruit}
          <Option value={fruit} selected={valueFilledEnhanced === fruit}>{fruit}</Option>
        {/each}
      </Select>
      <pre class="status">Selected: {valueFilledEnhanced}</pre>
    </Route>
  </main>
</Router>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>