<script>
  import { Item, Text } from '@smui/list';
  import Checkbox from '@smui/checkbox';
  import FormField from '@smui/form-field';

  export let statusItem = {};
</script>

<Item>
  <Text>{statusItem.name}</Text>
  {#each Array(statusItem.parts) as _, i}
    <FormField align="end">
      <Checkbox />
      <span slot="label">{ i + 1 }</span>
    </FormField>
  {/each}
</Item>
