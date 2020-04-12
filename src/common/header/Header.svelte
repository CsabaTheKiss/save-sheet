<script>
  import IconButton from '@smui/icon-button';
  import TopAppBar, { Row, Section, Title } from '@smui/top-app-bar';
  import { Route, Router, navigate } from 'svelte-routing';
</script>

<div class="top-app-bar-container">
  <TopAppBar variant="static">
    <Row>
      <Section>
        <IconButton class="material-icons">menu</IconButton>
        <Title>Static</Title>
      </Section>
      <Section align="end" toolbar>
        <IconButton class="material-icons" aria-label="Download">file_download</IconButton>
        <IconButton class="material-icons" aria-label="Print this page">print</IconButton>
        <IconButton class="material-icons" aria-label="Bookmark this page">bookmark</IconButton>
      </Section>
    </Row>
  </TopAppBar>
</div>