<template lang="html">
  <article v-if="beer">
    <h3>{{ beer.name }}</h3>
    <dl>
      <dt>Description:</dt>
      <dd>{{ beer.description }}</dd>

      <dt>ABV:</dt>
      <dd>{{ beer.abv }}</dd>

      <img :src="beer.image_url" alt="">
    </dl>
  </article>
</template>

<script>
export default {
  name: 'beer-detail',
  props: ['beer']
}
</script>

<style lang="css" scoped>
</style>
