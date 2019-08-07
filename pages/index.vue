<template>
  <v-layout style="margin: auto">
    <!-- <LogoIg /> -->
    <IgForm style="max-width: 40%" />
  </v-layout>
  
</template>

<script>
import Rabbit from '~/components/Rabbit.vue'
import IgForm from '~/components/IgForm.vue'
export default {
  components: {
    Rabbit,
    IgForm,
  }
}
</script>
