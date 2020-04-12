<script>
  import IconButton from '@smui/icon-button';
  import Button, { Label } from '@smui/button';
  import TopAppBar, { Row, Section, Title } from '@smui/top-app-bar';
  import { Route, Router, navigate, Link } from 'svelte-routing';

  export let pageTitle = '';
</script>

<div class="top-app-bar-container">
  <div class="header-decor">
    <img src="/header.png" alt="header-logo" />
  </div>
  <TopAppBar variant="static">
    <Row>
      <Section>
        <IconButton class="material-icons">menu</IconButton>
        <Title>
          <Link to="/">{pageTitle}</Link>
        </Title>
        <span class="header-nav-button">
          <Button on:click={() => navigate('/new-campaign')}>
            <Label>Start New Campaign</Label>
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

  .header-decor {
    background: black;
  }

  .header-decor img {
    width: 200px;
    height: auto;
  }
  
  @media (max-width: 640px) {
		.header-decor {
			display: none;
		}
	}
</style>