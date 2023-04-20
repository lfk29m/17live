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
