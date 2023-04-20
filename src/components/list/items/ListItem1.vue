<template>
  <div class="listitem">
    <p>Student: {{ item.name }}</p>
    <div>
      Year: {{item.year}}, Room: {{item.class}}
    </div>
  </div>
</template>

<script>
import ListItemMixins from "./ListItem"
export default {
  mixins: [ListItemMixins],
  name: 'ListItem1',
}
</script>