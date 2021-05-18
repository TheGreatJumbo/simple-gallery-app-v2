<template>
  <v-container fluid>
    <v-row>
      <v-col v-for="i in 4">
        <v-skeleton-loader elevation="1" type="card" min-width="300"/>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "Loader",
}
</script>

<style scoped>

</style>