<template lang="html">
  <ul>
    <beer-list-item v-for="(beer, index) in beers" :beer="beer" :key="index">{{beer.name}}</beer-list-item>
  </ul>
</template>

<script>

import BeerListItem from './BeerListItem.vue'

export default {
  name: 'beer-list',
  props: ['beers'],
  components: {
    "beer-list-item": BeerListItem
  }
}
</script>

<style lang="css" scoped>
  li{
    list-style: none;
  }
</style>
