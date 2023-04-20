<template>
  <div class="listitem">
    <span class="rank">{{ item.rank }}</span>
    <span>{{ item.winner }}</span>
  </div>
</template>

<script>
import ListItemMixins from "./ListItem"
export default {
  mixins: [ListItemMixins],
  name: 'ListItem2',
}
</script>