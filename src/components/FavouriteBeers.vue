<template lang="html">
  <div class="favourite-list">
    <h3>Favourite List</h3>
    <ul>
      <li v-for="beer in beers">{{beer.name}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'favourite-beers',
  props: ['beers']
}
</script>

<style lang="css" scoped>
  li{
    list-style: none;
  }

  p {
    text-decoration: underline;
  }
</style>
