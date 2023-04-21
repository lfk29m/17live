<template>
  <div :class="`list list--${type}`">
    <h1 v-if="type === 'type3'" class="title--type3">Top 3 Winners</h1>
    <slot :items="computedData"></slot>
  </div>
</template>

<script>
export  default  {
  name: "List2",
  props: {
    type: String,
    data: {
      type: Array,
      required: true,
    },
  },
  data: () => ({
    typeKeyMap: {
      'type1': 'name',
      'type2': 'title',
      'type3': 'winner',
    }
  }),
  computed: {
    computedData() {
      return this.data.map(item => {
        return {
          ...item,
          type: this.type,
          id: item[`${this.typeKeyMap[this.type]}`]
        }
      })
    },
  },
}
</script>