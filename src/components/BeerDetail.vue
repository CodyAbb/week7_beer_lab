<template lang="html">
  <article v-if="beer">
    <div class="outside-grid">
      <h3>{{ beer.name }}</h3>
      <button v-on:click="handleClick" type="button" name="button">Add To Favourites</button>
    </div>

    <dl>
      <div class="favourite-grid">
        <div class="description-grid">
          <dt>Description:</dt>
          <dd>{{ beer.description }}</dd>
          <dt>ABV:</dt>
          <dd>{{ beer.abv }}</dd>
        </div>
        <div class="image-grid">
          <img :src="beer.image_url" alt="">
        </div>
      </div>
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
  img {
    height: 300px;
  }

  .outside-grid{
    display: grid;
    grid-template-columns: auto auto;
  }

  .favourite-grid{
    display: grid;
    grid-template-columns: 50% 50%;
  }

  .image-grid{
    display: flex;
    justify-content: center;
    align-items: center;
  }
</style>
