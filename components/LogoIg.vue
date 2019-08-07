<template>
    <v-img
      :src="image"
      lazy-src="https://picsum.photos/id/11/10/6"
      aspect-ratio="1"
      class="grey lighten-2"
      max-width="500"
      max-height="300"
    ></v-img>
</template>

<script>
export default {
    name: 'ig-logo',
    components: {
    },
    data() {
      return {
        image: require('~/assets/images/Instagram-logo.jpg')
      }
    }
}
</script>
