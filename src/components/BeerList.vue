<template lang="html">
  <div class="list-of-beers">
    <h3>Brewdog's Inventory</h3>
    <ul>
      <beer-list-item v-for="(beer, index) in beers" :beer="beer" :key="index">{{beer.name}}</beer-list-item>
    </ul>
    <br>
    <p><i class="previous"></i> Previous</p>
    <p>Next <i class="next"></i></p>
  </div>
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

i{
  border: solid black;
  border-width: 0 3px 3px 0;
  display: inline-block;
  padding: 3px;
}

.previous {
  transform: rotate(135deg);
  -webkit-transform: rotate(135deg);
}

.next {
  transform: rotate(-45deg);
  -webkit-transform: rotate(-45deg);
}
</style>
