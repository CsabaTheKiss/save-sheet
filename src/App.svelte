<script>
  import Button, { Label } from '@smui/button';
  import { Route, Router, navigate } from 'svelte-routing';

  import Header from './common/header/Header.svelte';
  import NewCampaing from './new-campaing/NewCampaing.svelte';

  export let url = '';
</script>

<Router { url }>
  <Header></Header>
  <Route path="/new-campaing">
    <NewCampaing />
  </Route>
  <Route path="/">
    <p>Welcome to Save Sheet! Start a new campaign, or login to load an existing one.</p>
    <Button color="secondary" on:click={() => navigate('/new-campaing')} variant="unelevated">
      <Label>Start New Campaing</Label>
    </Button>
  </Route>
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