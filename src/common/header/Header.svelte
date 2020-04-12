<script>
  import IconButton from '@smui/icon-button';
  import Button, { Label } from '@smui/button';
  import TopAppBar, { Row, Section, Title } from '@smui/top-app-bar';
  import { Route, Router, navigate, Link } from 'svelte-routing';

  export let pageTitle = '';
</script>

<div class="top-app-bar-container">
  <TopAppBar variant="static">
    <Row>
      <Section>
        <IconButton class="material-icons">menu</IconButton>
        <Title>
          <Link to="/">{pageTitle}</Link>
        </Title>
        <span class="header-nav-button">
          <Button on:click={() => navigate('/new-campaing')}>
            <Label>Start New Campaing</Label>
          </Button>
        </span>
      </Section>
      <Section align="end" toolbar>
        <IconButton class="material-icons" aria-label="Download">file_download</IconButton>
        <IconButton class="material-icons" aria-label="Print this page">print</IconButton>
        <IconButton class="material-icons" aria-label="Bookmark this page">bookmark</IconButton>
      </Section>
    </Row>
  </TopAppBar>
</div>

<style>
	.header-nav-button {
		margin-left: 1em;
	}
</style>