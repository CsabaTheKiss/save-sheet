<script>
  import { Item, Text } from '@smui/list';
  import Checkbox from '@smui/checkbox';
  import FormField from '@smui/form-field';
  import { createEventDispatcher } from 'svelte';

  const dispatch = createEventDispatcher();

  export let statusItem = {};

  function clickHandler(changeObject) {
    dispatch('statusChange', changeObject);
  }
</script>

<Item>
  <Text>{statusItem.name}</Text>
  {#each Array(statusItem.parts) as _, i}
    <FormField align="end">
      <Checkbox on:click={(event) => clickHandler({ statusId: statusItem.id, partNumber: i + 1 , checked: event.target.checked })} />
      <span slot="label">{ i + 1 }</span>
    </FormField>
  {/each}
</Item>
