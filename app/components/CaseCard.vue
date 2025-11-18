<template>
  <NuxtLink
    class="case-card"
    :to="link"
    :aria-label="`查看案例：${headline}`"
    :style="cardStyle"
  >
    <div class="case-visual" aria-hidden="true">
      <div class="visual-overlay"></div>
      <div class="visual-caption">
        <h4>{{ overlayTitle }}</h4>
        <div class="tags" v-if="tagList.length">
          <span v-for="tag in tagList" :key="tag">{{ tag }}</span>
        </div>
      </div>
    </div>
    <div class="case-info">
      <p class="eyebrow" v-if="badge">{{ badge }}</p>
      <h3>{{ headline }}</h3>
      <p class="case-desc">{{ summary }}</p>
      <ul class="case-highlights">
        <li v-for="item in highlights" :key="item">
          <span class="dot"></span>
          <span>{{ item }}</span>
        </li>
      </ul>
      <div class="case-logos">
        <div
          v-for="logo in logoImages"
          :key="logo.id"
          class="logo-tile"
        >
          <img v-if="logo.src" :src="logo.src" :alt="logo.label" loading="lazy" />
          <span v-else>{{ logo.label }}</span>
        </div>
      </div>
    </div>
  </NuxtLink>
</template>

<script setup lang="ts">
import { computed } from 'vue'

const props = defineProps<{
  image: string
  link: string
  overlayTitle: string
  tags?: string[]
  badge?: string
  headline: string
  summary: string
  highlights: string[]
  logos?: { src?: string; label: string }[]
}>()

const logoImages = computed(() => {
  const base = props.logos ?? []
  const filled = [...base]
  while (filled.length < 3) {
    filled.push({ label: '品牌' })
  }
  return filled.map((item, index) => ({ ...item, id: `${item.label}-${index}` }))
})

const tagList = computed(() => props.tags ?? [])

const cardStyle = computed(() => ({
  '--case-image': `url(${props.image})`
}))
</script>

<style scoped>
.case-card {
  position: relative;
  display: grid;
  grid-template-columns: minmax(0, 3fr) minmax(320px, 2fr);
  border-radius: 26px;
  overflow: hidden;
  min-height: clamp(380px, 45vw, 520px);
  color: #ffffff;
  text-decoration: none;
  box-shadow: var(--shadow-soft);
  transition: transform 0.25s ease, box-shadow 0.25s ease;
  background-image: var(--case-image);
  background-size: cover;
  background-position: center;
  width: 100%;
  max-width: 100%;
  margin: 0 auto;
}

.case-card:focus-visible {
  outline: 3px solid var(--color-orange);
  outline-offset: 4px;
}

.case-card:hover,
.case-card:focus-visible {
  box-shadow: 0 30px 60px rgba(15, 23, 42, 0.35);
  transform: translateY(-4px);
}

.case-visual {
  position: relative;
  overflow: hidden;
  backdrop-filter: blur(2px);
}

.visual-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(180deg, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.4));
}

.visual-caption {
  position: absolute;
  left: 0;
  right: 0;
  bottom: 0;
  padding: 1.5rem 2rem;
  display: grid;
  gap: 0.75rem;
}

.visual-caption h4 {
  margin: 0;
  font-size: clamp(1.2rem, 2vw, 1.6rem);
  color: #fff;
}

.tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.tags span {
  padding: 0.3rem 0.9rem;
  border-radius: var(--radius-pill);
  background: rgba(0, 0, 0, 0.35);
  border: 1px solid rgba(255, 255, 255, 0.35);
  font-size: 0.85rem;
}

.case-info {
  position: relative;
  padding: clamp(1.5rem, 3vw, 2.5rem);
  display: grid;
  gap: 1rem;
  isolation: isolate;
}

.case-info::before {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(135deg, rgba(13, 13, 18, 0.75), rgba(13, 13, 18, 0.6));
  backdrop-filter: blur(6px);
  z-index: -1;
}

.eyebrow {
  margin: 0;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  font-size: 0.8rem;
  color: rgba(255, 255, 255, 0.72);
}

.case-desc {
  margin: 0;
  color: rgba(255, 255, 255, 0.92);
  line-height: 1.6;
}

h3 {
  margin: 0;
  font-size: clamp(2rem, 3vw, 2.8rem);
  color: #ffffff;
}

.case-highlights {
  margin: 0;
  padding: 0;
  list-style: none;
  display: grid;
  gap: 0.6rem;
}

.case-highlights li {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  color: rgba(255, 255, 255, 0.9);
}

.dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: var(--color-orange);
  flex-shrink: 0;
}

.case-logos {
  display: flex;
  gap: 0.75rem;
  margin-top: 0.5rem;
  flex-wrap: wrap;
}

.logo-tile {
  width: 96px;
  height: 64px;
  border-radius: 16px;
  background: rgba(255, 255, 255, 0.16);
  border: 1px solid rgba(255, 255, 255, 0.32);
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 0.5rem;
}

.logo-tile img {
  width: 100%;
  height: 100%;
  object-fit: contain;
}

@media (max-width: 960px) {
  .case-card {
    grid-template-columns: 1fr;
  }

  .case-info {
    padding: 2rem;
  }
}
</style>
