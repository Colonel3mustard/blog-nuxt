<template>
  <v-row fluid class="row-1">
    <h1 class="header">Recent Posts:</h1>
    <v-row fluid class="row-2">
    <v-col class="col" fluid v-for="article of articles" :key="article.key" >
    <v-card elevation="2" class="article" color="accent" max-width="250" >
      <v-img
      class="white--text align-end"
      max-height="250"
      max-width="250"
      :src="require(`~/static/resources/${article.img}`)"
    ><v-card-title>{{article.title}}</v-card-title></v-img>

  
  <v-card-text>{{article.description}}</v-card-text>
    <v-card-actions>
      <v-btn
        text
        color="amber accent-4"
        @click="reveal = true"
        :to="`blog/${article.slug}`" nuxt
      >
        Read Post
      </v-btn>
      <v-btn
        text
        color="amber accent-4"
      ><v-icon>
        mdi-share-variant
        </v-icon>
      </v-btn>
    </v-card-actions>
      </v-card>
    </v-col>
    </v-row>
  </v-row>
</template>

<script>

export default {
  async asyncData({ $content, params }) {
        const articles = await $content('blog', params.slug)
        .only(['title', 'description', 'img', 'slug'])
        .sortBy('createdAt', 'asc')
        .fetch();

        return { articles }
    }
}
</script>

<style scoped>
.article {
  font-family: 'Montserrat', sans-serif;
}
.header {
  font-family: 'Montserrat', sans-serif;
}
.row-1 {
  justify-content: center;
}
</style>
