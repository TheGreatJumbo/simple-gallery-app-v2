<template>
  <Loader v-if="Loading"/>
  <Alert v-else-if="alert"/>
  <v-container fluid v-else>
    <v-app-bar-title class="text-center">Галерея</v-app-bar-title>
    <hr>
    <v-row justify="center">
      <v-col v-for="i in 4" :key="i">
          <v-app-bar-title class="text-center">Категория {{i}}</v-app-bar-title>
          <v-row v-for="Photo in Photos[`${i}`]">
            <v-col class="d-flex justify-center">
              <Images :source="Photo.url" :id="Photo.id"/>
            </v-col>
          </v-row>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import Loader from "../components/Loader";
import Images from "../components/Images";
import Alert from "../components/Alert";

export default {
  name: 'Home',
  components: {Alert, Images, Loader},
  data() {
    const Loading = true

    return {
      Loading
    }
  },
  computed: {
    alert() {
      return this.$store.state.Alert
    },
    Photos() {
      return {
        1: this.$store.state.Category1,
        2: this.$store.state.Category2,
        3: this.$store.state.Category3,
        4: this.$store.state.Category4
      }
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
