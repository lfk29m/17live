<template>
  <div>
    <List :data="type1"/>
    <List :data="type2"/>
    <List :data="type3"/>
  </div>
</template>

<script>
import List from "@/components/list/List.vue"

export default {
  name: "Home",
  components: {
    List,
  },
  data: () => ({
    type1: [
      {
        name: "Anna",
        year: 10,
        class: "A"
      },
      {
        name: "Mark",
        year: 10,
        class: "M",
      }
    ],
    type2: [
      {
        title: "Javascript Info",
        category: "book",
        rating: 10,
      },
      {
        title: "Fantasy",
        category: "movie",
        rating: 5,
      }
    ],
    type3: [
      {
        winner: 'Amy',
        rank: 1
      },
      {
        winner: 'Bob',
        rank: 2
      },
      {
        winner: 'Jack',
        rank: 2
      }
    ]
  }),
};
</script>
