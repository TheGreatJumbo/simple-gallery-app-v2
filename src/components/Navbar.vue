<template>
  <div>
    <v-navigation-drawer app v-model="drawer" temporary>
      <v-list-item>
        <v-list-item-avatar>
          <v-img src="https://avatars.githubusercontent.com/u/45094721?v=4"></v-img>
        </v-list-item-avatar>

        <v-list-item-content>
          <v-list-item-title>Антон</v-list-item-title>
          <v-list-item-subtitle>hasenpostxii@gmail.com</v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>

      <v-divider/>

      <v-list dense>
        <v-list-item :to="item.to" v-for="item in items" :key="item.title" link>
          <v-list-item-icon><v-icon>{{ item.icon }}</v-icon></v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar dense app @click.stop="drawer = !drawer">
      <v-app-bar-nav-icon/>
    </v-app-bar>

  </div>
</template>

<script>
export default {
name: "Navbar",
  data () {
    return {
      drawer: null,
      items: [
        { title: 'Галерея', icon: 'mdi-image', to: '/' },
        { title: 'Обо мне', icon: 'mdi-account', to: '/about' },
      ],
    }
  },
}
</script>

<style scoped>

</style>