<template>
  <section class="platform-card">
    <header>
      <h2>{{ title }}</h2>
      <p>{{ description }}</p>
    </header>
    <ul>
      <li v-for="item in features" :key="item">
        {{ item }}
      </li>
    </ul>
    <NuxtLink class="detail-link" :to="detailRoute">
      产品定价详情
    </NuxtLink>
  </section>
</template>

<script setup lang="ts">
defineProps<{
  title: string
  description: string
  detailRoute: string
  features: string[]
}>()
</script>

<style scoped>
.platform-card {
  display: grid;
  gap: 1.25rem;
  padding: 2rem;
  border-radius: 18px;
  background: var(--color-surface);
  box-shadow: var(--shadow-soft);
  border: 1px solid rgba(148, 163, 184, 0.18);
}

.platform-card header h2 {
  margin: 0 0 0.75rem;
  font-size: 1.5rem;
}

.platform-card header p {
  margin: 0;
  color: var(--color-text-muted);
  line-height: 1.6;
}

.platform-card ul {
  margin: 0;
  padding-left: 1.1rem;
  display: grid;
  gap: 0.5rem;
  color: var(--color-text-primary);
}

.detail-link {
  justify-self: flex-start;
  padding: 0.65rem 1.4rem;
  border-radius: var(--radius-pill);
  border: 1px solid var(--color-brand);
  color: var(--color-brand);
  text-decoration: none;
  font-weight: 600;
  transition: transform 0.2s ease, background 0.2s ease, color 0.2s ease;
}

.detail-link:hover {
  transform: translateY(-2px);
  background: rgba(14, 165, 233, 0.08);
}
</style>
