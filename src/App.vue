<template>
  <v-app>
    <Navbar/>
    <v-main>
      <router-view/>
    </v-main>
    <v-footer v-if="$route.path !== '/about'" padless>
      <v-col class="text-center" cols="12">
        источник: <a href="http://jsonplaceholder.typicode.com/">jsonplaceholder.typicode.com</a>
      </v-col>
    </v-footer>
  </v-app>
</template>

<script>

import Navbar from "./components/Navbar";
export default {
  name: 'App',
  components: {Navbar},
  data: () => ({
    //
  }),
};
</script>
