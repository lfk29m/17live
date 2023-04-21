<template>
  <div id="app">
    <router-view />
  </div>
</template>

<style lang="scss">
p {
  margin: 0 0 1rem 0;
}

.block {
  margin-bottom: 2rem;
}

.list {
  padding: 1rem;
  margin-bottom: 1rem;
}
.list--type1,
.list--type2 {
  background-color: #efefef;
}
.list--type3 {
  background-color: #000000;
}
.listitem {
  border-radius: 10px;
  margin-bottom: 0.8rem;
  padding: 1rem;
  background-color: #ffffff;
  &:last-child {
    margin-bottom: 0;
  }
}

.rank {
  margin-right: 0.5rem;
}

.title--type3 {
  color: #ffffff;
}
</style>