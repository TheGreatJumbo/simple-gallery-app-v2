<template>
  <DetailsLoader v-if="Loading"/>

  <v-container fluid v-else-if="Photo">
    <v-card>
      <v-app-bar-title class="text-center">{{Photo.title}}</v-app-bar-title>
      <v-img :src="Photo.url"/>
      <v-app-bar-title class="text-center">Категория: {{Photo.albumId}} Идентификатор: {{Photo.id}}</v-app-bar-title>
      <v-app-bar-title class="text-center">ссылка: <a :href="Photo.url">{{Photo.url}}</a></v-app-bar-title>
    </v-card>
  </v-container>

  <v-container fluid v-else>
    <v-card color="red">
      <v-app-bar-title class="text-center">В галерее отсутствует изображение с идентификатором {{PhotoID}}</v-app-bar-title>
    </v-card>
  </v-container>
</template>

<script>
import Loader from "../components/Loader";
import DetailsLoader from "../components/DetailsLoader";

export default {
  name: "Details",
  components: {DetailsLoader, Loader},
  data() {
    const Loading = true
    const PhotoID = this.$route.params.id
    return {
      Loading, PhotoID
    }
  },
  computed: {
    Photo() {
      const PhotoID = this.$route.params.id
      const Category = Math.trunc(parseInt(PhotoID, 10) / 50) + 1
      return this.$store.state[`Category${Category}`]?.find(ph => ph.id == PhotoID)
    }
  },
  async mounted() {
    if (!this.$store.state.AppLoaded) {
      await this.$store.dispatch('LoadPhotos')
      setTimeout(() => this.Loading = false, 500)
    } else this.Loading = false
  }
}
</script>

<style scoped>

</style>