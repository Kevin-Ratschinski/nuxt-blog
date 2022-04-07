<template>
  <article class="container mx-auto mt-8">
    <h2 class="mb-2 text-2xl font-medium text-gray-900 title-font">
      {{ article.title }}
    </h2>

    <nuxt-content :document="article" />
  </article>
</template>

<script lang="ts">
import { Vue, Component } from 'nuxt-property-decorator'
import { Context } from '@nuxt/types'

@Component
export default class BlogArticlePage extends Vue {
  async asyncData ({ $content, params }: Context) {
    const article = await $content(params.slug).fetch()
    return { article }
  }
}
</script>

<style>
.nuxt-content p {
  margin-top: 10px;
}
</style>
