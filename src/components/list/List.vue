<template>
 <div :class="`list list--${type}`">
   <h1 v-if="type === 'type3'" class="title--type3">Top 3 Winners</h1>
   <component
     v-for="item in computedData"
     :key="item.id"
     :is="itemComponent"
     :item="item"
   ></component>
 </div>
</template>

<script>
import ListItem from "@/components/list/items/ListItem1.vue"
export default {
  name: "List",
  props: {
    data: {
      type: Array,
      required: true,
    }
  },
  components: {
    ListItem
  },
  data: () => ({
    typeKeyMap: {
      'type1': 'name',
      'type2': 'title',
      'type3': 'winner',
    }
  }),
  computed: {
    type() {
      if(!Array.isArray(this.data)) return null
      const item = this.data[0]
      return this.getType(item)
    },
    computedData() {
      return this.data.map(item => {
        const type = this.getType(item)
        return {
          ...item,
          type,
          id: item[`${this.typeKeyMap[type]}`]
        }
      })
    },
    itemComponent() {
      if(this.type === 'type1') return () => import('./items/ListItem1.vue')
      if(this.type === 'type2') return () => import('./items/ListItem2.vue')
      if(this.type === 'type3') return () => import('./items/ListItem3.vue')
      return null
    },
  },
  methods: {
    getType(item) {
      if(!item) return null
      if(Object.hasOwn(item, 'name')) return "type1"
      if(Object.hasOwn(item, 'title')) return "type2"
      return "type3"
    },
  },
};
</script>

<style lang="scss">

</style>