<template lang="html">
  <ul>
    <li v-for="beer in beers" :value="beer">{{beer.name}}</li>
  </ul>
</template>

<script>
export default {
  name: 'beer-list',
  props: ['beers']
}
</script>

<style lang="css" scoped>
  li{
    list-style: none;
  }
</style>
