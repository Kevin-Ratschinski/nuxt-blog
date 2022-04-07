<template>
<div class="container mx-auto">
  <h1 class="my-8 text-5xl font-bold">
    Mein Blog
  </h1>

  <Article
    v-for="article in articles"
    :key="article.id"
    :category="article.category"
    :date="formatDate(article.createdAt)"
    :to="article.slug">
  <template #title>
    {{ article.title }}
  </template>
  {{ article.description }}
  </Article>
</div>
</template>

<script lang="ts">
import { Vue, Component } from 'nuxt-property-decorator'
import { Context } from '@nuxt/types'
import Article from '~/components/Article.vue'

@Component({
  components: {
    Article
  }
})
export default class IndexPage extends Vue {
  async asyncData ({ $content }: Context) {
    const articles = await $content().fetch()
    return { articles }
  }

  private formatDate (date: string): string {
    return new Date(date).toLocaleDateString('de-DE',
      {
        weekday: 'long',
        year: 'numeric',
        month: 'long',
        day: 'numeric'
      })
  }
}
</script>
