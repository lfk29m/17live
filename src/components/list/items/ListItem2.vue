<template>
  <div class="listitem">
    <p>Title: {{ item.title }}</p>
    <div>
      Category: {{item.category}} | {{item.rating}} likes
    </div>
  </div>
</template>

<script>
import ListItemMixins from "./ListItem"
export default {
  mixins: [ListItemMixins],
  name: 'ListItem2',
}
</script>