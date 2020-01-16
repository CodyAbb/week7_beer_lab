<template>
  <div id="app">
    <h1>Brewdog Beers</h1>
    <div class="container">
      <beer-list :beers='beers'></beer-list>
    </div>
  </div>
</template>

<script>

import{eventBus} from './main.js';
import BeerList from './components/BeerList.vue'

export default {
  name: 'app',
  data() {
    return{
      beers: [],
      selectedBeerId: null,
      renderedBeer: {}
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
    "beer-list": BeerList
  },
  computed: {
    renderBeer: function() {
      const result = this.beers.find(beer => beer.id === this.selectedBeerId)
      return this.renderedBeer = result
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
