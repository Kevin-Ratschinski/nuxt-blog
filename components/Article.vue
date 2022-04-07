<template>
  <div class="flex flex-wrap py-8 border-t-2 border-gray-200 md:flex-no-wrap">
    <div class="flex flex-col flex-shrink-0 mb-6 md:w-64 md:mb-0">
      <span class="font-medium tracking-widest text-gray-900 title-font">{{ category }}</span>
      <span class="mt-1 text-sm text-gray-500">{{ date }}</span>
    </div>
    <div class="md:flex-grow">
      <h2 class="mb-2 text-2xl font-medium text-gray-900 title-font">
        <slot name="title" />
      </h2>
      <p class="leading-relaxed">
        <slot />
      </p>
      <nuxt-link v-bind="$attrs" class="inline-flex items-center mt-4 text-indigo-500">
        Mehr erfahren
        <svg
          class="w-4 h-4 ml-2"
          viewBox="0 0 24 24"
          stroke="currentColor"
          stroke-width="2"
          fill="none"
          stroke-linecap="round"
          stroke-linejoin="round"
        >
          <path d="M5 12h14" />
          <path d="M12 5l7 7-7 7" />
        </svg>
      </nuxt-link>
    </div>
  </div>
</template>

<script lang="ts">
import { Vue, Component, Prop } from 'nuxt-property-decorator'

@Component
export default class Article extends Vue {
  @Prop({ type: String, required: true })
  private category!: string

  @Prop({ type: String, required: true })
  private date!: string
}
</script>
