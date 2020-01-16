<template>
  <div id="app">
    <h1>Brewdog Beers</h1>
    <div class="container">
      <beer-list :beers='beers'></beer-list>
      <beer-detail :beer='renderedBeer'></beer-detail>
      <favourite-beers :beers='favouriteBeersArray'></favourite-beers>
    </div>
  </div>
</template>

<script>

import{eventBus} from './main.js';
import BeerList from './components/BeerList.vue'
import BeerDetail from './components/BeerDetail.vue'
import FavouriteBeers from './components/FavouriteBeers.vue'

export default {
  name: 'app',
  data() {
    return{
      beers: [],
      selectedBeerId: null,
      favouriteBeersArray: [],
      pageNumber: "1"
      // brewdogApiUrl: `https://api.punkapi.com/v2/beers?page=1&per_page=25`

    }
  },
  methods: {
    fetchData() {
      // let apiurl = `https://api.punkapi.com/v2/beers?page=${this.pageNumber}&per_page=25`
      fetch('https://api.punkapi.com/v2/beers?page=1&per_page=25')
      .then(response => response.json())
      .then(beerArray => this.beers = beerArray);
    }
  },
  mounted(){
    this.fetchData();

    eventBus.$on('beer-selected', (beerId) => {
      this.selectedBeerId = beerId
    })

    eventBus.$on('favourite-beer-selected', (beer) => {
      this.favouriteBeersArray.push(beer)
    })

    eventBus.$on('next-page-select', (amount) =>{

    })
  },

  components: {
    "beer-list": BeerList,
    "beer-detail": BeerDetail,
    "favourite-beers": FavouriteBeers
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
  text-align: left;
  color: #2c3e50;
  margin-top: 60px;
  width: 90%;
}

h1 {
  text-align: center;
  margin-bottom: 50px;
  font-size: 2em;
}

.container {
  display: grid;
  grid-template-columns: auto auto auto;
  grid-column-gap: 100px
}
</style>
