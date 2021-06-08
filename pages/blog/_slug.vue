<template>
    <article>
        <v-row>
        <v-col offset="2" w="8">
          <nuxt-content :document="article" />
        </v-col>
      </v-row>
    </article>
</template>

<script>
export default {
    async asyncData({ $content, params }) {
        const article = await $content('blog', params.slug).fetch();

        return { article }
    }
}
</script>

<style scoped>

</style>