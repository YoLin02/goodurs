<script setup lang="ts">
import { computed } from 'vue'

const route = useRoute()
const slug = computed(() => String(route.params.slug ?? ''))
</script>

<template>
  <article class="detail-page">
    <header>
      <p class="eyebrow">解决方案</p>
      <h1>{{ slug.toUpperCase() }} 能力介绍</h1>
      <p>此页面暂为占位，用于承载 {{ slug }} 解决方案的详细说明。</p>
    </header>
    <NuxtLink class="back-link" to="/pricing">查看全部产品</NuxtLink>
  </article>
</template>

<style scoped>
.detail-page {
  max-width: 900px;
  margin: 0 auto;
  display: grid;
  gap: 1.25rem;
}

h1 {
  margin: 0;
  font-size: clamp(2.2rem, 5vw, 3rem);
  color: var(--color-navy);
}

.eyebrow {
  font-size: 0.85rem;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  color: var(--color-brand);
  margin: 0;
}

p {
  margin: 0;
  color: var(--color-text-muted);
  line-height: 1.6;
}

.back-link {
  justify-self: flex-start;
  color: var(--color-brand);
  text-decoration: none;
  font-weight: 600;
}
</style>
