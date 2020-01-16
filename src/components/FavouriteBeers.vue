<template lang="html">
  <ul>
    <li v-for="beer in beers">{{beer.name}}</li>
  </ul>
</template>

<script>
export default {
  name: 'favourite-beers',
  props: ['beers']
}
</script>

<style lang="css" scoped>
</style>
