<template>
  <section class="case-grid">
    <CaseCard
      v-for="item in normalizedCases"
      :key="item.link"
      v-bind="item"
    />
  </section>
</template>

<script setup lang="ts">
import { computed } from 'vue'

type CaseItem = {
  title: string
  description: string
  image: string
  link: string
  tags?: string[]
  highlights?: string[]
  logos?: { src?: string; label: string }[]
  logo?: string
  badge?: string
  overlayTitle?: string
  headline?: string
  summary?: string
}

const props = defineProps<{
  cases: CaseItem[]
}>()

const normalizedCases = computed(() =>
  props.cases.map((item) => ({
    image: item.image,
    link: item.link,
    overlayTitle: item.overlayTitle ?? item.title,
    tags: item.tags ?? [],
    badge: item.badge,
    headline: item.headline ?? item.title,
    summary: item.summary ?? item.description,
    highlights: item.highlights ?? [],
    logos:
      item.logos ??
      (item.logo ? [{ src: item.logo, label: item.title }] : undefined)
  }))
)
</script>

<style scoped>
.case-grid {
  display: grid;
  gap: 1.75rem;
  grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
}
</style>
