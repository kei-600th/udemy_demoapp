<template>
  <v-app>
    <logged-in-app-bar
    ＃navigation-toggle-button
    >
      <v-app-bar-nav-icon
      @click="drawer = !drawer"
      />
    </logged-in-app-bar>
    <project-navigation-drawer />
    <v-main>
      <nuxt />
    </v-main>
    <app-footer />
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      drawer: null
    }
  }
}
</script>
