<template>
  <v-app>
    
    <v-app-bar
      fixed
      app
    >
    <v-btn :to="`/`" nuxt>
      <v-icon>mdi-checkbox-multiple-blank-circle-outline</v-icon>
    </v-btn>
    <v-spacer />
      <v-toolbar-title id="title" v-text="title" />
      <v-spacer />
      
    </v-app-bar>
    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>
    <v-footer
      :absolute="!fixed"
      app
    >
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>

export default {
  data () {
    return {
      fixed: false,
      title: 'Nota Bene Wellness'
    }
  }
}
</script>

<style scoped>
#title {
  font-family: 'Shadows Into Light', cursive;
  font-size: 2em;
}
</style>