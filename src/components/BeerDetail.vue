<template lang="html">
  <article v-if="beer">
    <h3>{{ beer.name }}</h3>
    <dl>
      <dt>Description:</dt>
      <dd>{{ beer.description }}</dd>

      <dt>ABV:</dt>
      <dd>{{ beer.abv }}</dd>

      <img :src="beer.image_url" alt="">

      <button v-on:click="handleClick" type="button" name="button">Add To Favourites</button>
    </dl>
  </article>
</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'beer-detail',
  props: ['beer'],
  methods: {
    handleClick(){
      eventBus.$emit('favourite-beer-selected', this.beer)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
