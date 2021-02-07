<template>
  <v-app dark>
    <v-app-bar fixed app>
      <v-app-bar-nav-icon />
      <v-toolbar-title>
        <nuxt-link to="/">Weather App</nuxt-link>
      </v-toolbar-title>
      <v-spacer />
      <v-btn text>
        <nuxt-link to="/about">About</nuxt-link>
      </v-btn>
    </v-app-bar>
    <v-main>
      <v-container>
        <nuxt />
      </v-container>
    </v-main>

    <v-footer app>
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {};
</script>

<style scoped>
.v-application a {
  text-decoration: none;
  color: white;
}
a.nuxt-link-exact-active {
  color: #42b983;
}
</style>
