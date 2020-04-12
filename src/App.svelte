<script>
  import { Route, Router, navigate } from 'svelte-routing';

  import Header from './common/header/Header.svelte';
  import NewCampaign from './new-campaign/NewCampaign.svelte';
  import Campaign from './campaign/Campaign.svelte'

  export let url = '';
</script>

<Router { url }>
  <Header pageTitle="Save sheet"></Header>
  <div class="main">
    <Route path="/new-campaign">
      <NewCampaign />
    </Route>
    <Route path="/campaign/:capmaignId" let:params>
      <Campaign capmaignId="{ params.capmaignId }" />
    </Route>
    <Route path="/">
      <p class="mdc-typography--body1">Welcome to Save Sheet! Start a new campaign, or login to load an existing one.</p>
    </Route>
  </div>
</Router>

<style>
	.main {
		padding: 1em;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>