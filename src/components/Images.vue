<template>
  <v-hover v-slot="{ hover }">
    <v-img :src="source" max-width="300" contain>

      <template v-slot:placeholder>
        <v-row class="fill-height ma-0" align="center" justify="center">
          <v-progress-circular indeterminate color="grey lighten-5"/>
        </v-row>
      </template>

      <v-overlay absolute :value="hover">
        <v-btn @click="$router.push(`/details/${id}`)">Подробнее</v-btn>
      </v-overlay>

    </v-img>
  </v-hover>
</template>

<script>
export default {
  name: "Image",
  props: {
    source: String,
    id: Number
  }
}
</script>

<style scoped>

</style>