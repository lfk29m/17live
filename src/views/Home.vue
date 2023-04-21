<template>
  <div>
    <section class="block">
      <h1>第一種寫法</h1>
      <List :data="type1"/>
      <List :data="type2"/>
      <List :data="type3"/>
    </section>

    <section class="block">
      <h1>第二種寫法</h1>
      <List2 type="type1" :data="type1">
        <template v-slot:default="{items}">
          <ListItem1
            v-for="item in items"
            :key="item.id"
            :item="item"
          />
        </template>
      </List2>
      <List2 type="type2" :data="type2">
        <template v-slot:default="{items}">
          <ListItem2
            v-for="item in items"
            :key="item.id"
            :item="item"
          />
        </template>
      </List2>
      <List2 type="type3" :data="type3">
        <template v-slot:default="{items}">
          <ListItem3
            v-for="item in items"
            :key="item.id"
            :item="item"
          />
        </template>
      </List2>
    </section>
  </div>
</template>

<script>
import List from "@/components/list/List.vue"
import List2 from "@/components/list/List2.vue";

export default {
  name: "Home",
  components: {
    ListItem1: () => import('@/components/list/items/ListItem1.vue'), // 動態引入, 有需要才會去加載元件
    ListItem2: () => import('@/components/list/items/ListItem2.vue'),
    ListItem3: () => import('@/components/list/items/ListItem3.vue'),
    List2,
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
    ],
  }),
  methods: {
    solution(recipes) {
      if(recipes.length > 500 || recipes.length < 1) return

      let map = {}

      for(let i=0; i < recipes.length; i++) {
        const recipe = recipes[i]
        const recipeLen = recipe.length
        if(recipeLen > 10 || recipeLen < 2) return

        const food = this.capitalizeFirstLetter(recipe[0])
        if(!this.isValidLength(food)) return

        const sources = recipe.slice(1).map(source => this.capitalizeFirstLetter(source))
        for(const source of sources) {
          if(!this.isValidLength(source)) return
          map[source] = map[source] ? [...map[source], food] : [food]
        }
      }

      const result = []

      for(let source in map) {
        const array = [source, ...map[source]]
        result.push(array)
      }

      result.sort((a, b) => {
        if (a[0] < b[0]) {
          return -1;
        } else if (a[0] > b[0]) {
          return 1;
        } else {
          return 0;
        }
      })

      return result
    },
    capitalizeFirstLetter(string) {
      return string.charAt(0).toUpperCase() + string.slice(1);
    },
    isValidLength(str) {
      if(str.length < 1) return false
      if(str.length > 50) return false
      return true
    },
  },
  created() {
    const recipes = [
      ["Salad", "Tomato", "Cucumber", "Salad", "Sauce"],
      ["Pizza", "Tomato", "Sausage", "Sauce", "Dough"],
      ["Quesadilla", "Chicken", "Cheese", "Sauce"],
      ["Sandwich", "Salad", "Bread", "Tomato", "Cheese"]
    ]
    const result = this.solution(recipes)
    console.log(result)
  },
};
</script>
