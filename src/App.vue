<template>
  <div id="app">
    <h1>Brewdog Beers</h1>
    <div class="container">
      <beer-list :beers='beers'></beer-list>
      <beer-detail :beer='renderedBeer'></beer-detail>
    </div>
  </div>
</template>

<script>

import{eventBus} from './main.js';
import BeerList from './components/BeerList.vue'
import BeerDetail from './components/BeerDetail.vue'

export default {
  name: 'app',
  data() {
    return{
      beers: [],
      selectedBeerId: null
    }
  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
      .then(response => response.json())
      .then(beerArray => this.beers = beerArray)

    eventBus.$on('beer-selected', (beerId) => {
      this.selectedBeerId = beerId
    })
  },
  components: {
    "beer-list": BeerList,
    "beer-detail": BeerDetail
  },
  computed: {
    renderedBeer: function() {
      return this.beers.find(beer => beer.id === this.selectedBeerId)
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
