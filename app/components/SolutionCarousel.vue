<template>
  <section
    class="solution-carousel"
    @mouseenter="pauseAuto"
    @mouseleave="resumeAuto"
  >
    <header class="carousel-head">
      <div class="carousel-meta">
        <span class="eyebrow">{{ headline }}</span>
        <h2>{{ title }}</h2>
      </div>
      <div class="carousel-side">
        <p class="carousel-description">{{ description }}</p>
        <NuxtLink :to="ctaLink" class="carousel-cta">
          {{ ctaLabel }}
        </NuxtLink>
      </div>
    </header>

    <div class="carousel-stage">
      <button
        type="button"
        class="nav-btn prev"
        aria-label="上一项"
        @click="prev"
      >
        <svg viewBox="0 0 24 24" aria-hidden="true">
          <path d="M15 6l-6 6 6 6" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" />
        </svg>
      </button>

      <div class="card-track">
        <article
          v-for="(item, index) in items"
          :key="item.title"
          :class="['carousel-card', cardState(index)]"
        >
          <div class="card-visual">
            <img :src="item.image" :alt="item.title" loading="lazy" />
          </div>
          <div class="card-body">
            <span class="chip" v-if="item.label">{{ item.label }}</span>
            <h3>{{ item.title }}</h3>
            <p>{{ item.subtitle }}</p>
            <NuxtLink :to="item.link" class="card-link">了解更多</NuxtLink>
          </div>
        </article>
      </div>

      <button
        type="button"
        class="nav-btn next"
        aria-label="下一项"
        @click="next"
      >
        <svg viewBox="0 0 24 24" aria-hidden="true">
          <path d="M9 6l6 6-6 6" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" />
        </svg>
      </button>
    </div>

    <div class="carousel-controls">
      <div class="dots" role="tablist">
        <button
          v-for="(item, index) in items"
          :key="item.title"
          type="button"
          role="tab"
          :aria-label="`切换至 ${item.title}`"
          :aria-selected="index === activeIndex"
          :class="['dot', { active: index === activeIndex }]"
          @click="select(index)"
        />
      </div>
      <button
        type="button"
        class="play-btn"
        :aria-label="isPlaying ? '暂停自动播放' : '恢复自动播放'"
        @click="togglePlay"
      >
        <svg v-if="isPlaying" viewBox="0 0 24 24" aria-hidden="true">
          <path d="M8 5h2.5v14H8zM13.5 5H16v14h-2.5z" fill="currentColor" />
        </svg>
        <svg v-else viewBox="0 0 24 24" aria-hidden="true">
          <path d="M9 5l10 7-10 7V5z" fill="currentColor" />
        </svg>
      </button>
    </div>
  </section>
</template>

<script setup lang="ts">
import { computed, onBeforeUnmount, onMounted, ref, watch } from 'vue'

type CarouselItem = {
  title: string
  subtitle: string
  image: string
  link: string
  label?: string
}

const props = withDefaults(
  defineProps<{
    items: CarouselItem[]
    title: string
    headline?: string
    description?: string
    ctaLabel?: string
    ctaLink?: string
    interval?: number
  }>(),
  {
    headline: '解决方案精选',
    description: '',
    ctaLabel: '探索更多',
    ctaLink: '/pricing',
    interval: 6000
  }
)

const activeIndex = ref(0)
const isPlaying = ref(true)
const timer = ref<number | null>(null)

const count = computed(() => props.items.length)

const next = () => {
  activeIndex.value = (activeIndex.value + 1) % count.value
}

const prev = () => {
  activeIndex.value = (activeIndex.value - 1 + count.value) % count.value
}

const select = (index: number) => {
  activeIndex.value = index
  resetAuto()
}

const startAuto = () => {
  stopAuto()
  if (isPlaying.value && count.value > 1) {
    timer.value = window.setInterval(next, props.interval)
  }
}

const stopAuto = () => {
  if (timer.value !== null) {
    clearInterval(timer.value)
    timer.value = null
  }
}

const resetAuto = () => {
  if (isPlaying.value) startAuto()
}

const pauseAuto = () => {
  stopAuto()
}

const resumeAuto = () => {
  if (isPlaying.value) startAuto()
}

const togglePlay = () => {
  isPlaying.value = !isPlaying.value
  if (isPlaying.value) startAuto()
  else stopAuto()
}

const cardState = (index: number) => {
  if (index === activeIndex.value) return 'is-active'
  const prevIndex = (activeIndex.value - 1 + count.value) % count.value
  const nextIndex = (activeIndex.value + 1) % count.value
  if (index === prevIndex) return 'is-prev'
  if (index === nextIndex) return 'is-next'
  return 'is-rest'
}

onMounted(startAuto)
onBeforeUnmount(stopAuto)

watch(
  () => props.items,
  () => {
    activeIndex.value = 0
    startAuto()
  },
  { deep: true }
)
</script>

<style scoped>
.solution-carousel {
  width: 100%;
  background: linear-gradient(120deg, #ffd2df 0%, #fcb69f 45%, #f9825d 100%);
  border-radius: 0;
  padding: clamp(2rem, 5vw, 3.25rem);
  display: grid;
  gap: clamp(1.5rem, 4vw, 2.8rem);
  box-shadow: none;
  color: #1d1327;
}

.carousel-head {
  display: grid;
  grid-template-columns: minmax(0, 1.4fr) minmax(0, 1fr);
  gap: clamp(1.5rem, 4vw, 3rem);
  align-items: flex-start;
}

.carousel-meta {
  display: grid;
  gap: 0.85rem;
}

.carousel-meta h2 {
  margin: 0;
  font-size: clamp(2.2rem, 4vw, 3rem);
  color: #1b1325;
  font-weight: 600;
  letter-spacing: -0.01em;
  line-height: 1.2;
}

.eyebrow {
  font-size: 0.85rem;
  text-transform: uppercase;
  letter-spacing: 0.18em;
  color: rgba(27, 19, 37, 0.6);
}

.carousel-side {
  display: grid;
  gap: 1rem;
}

.carousel-description {
  margin: 0;
  color: rgba(27, 19, 37, 0.85);
  line-height: 1.7;
  font-size: 1rem;
}

.carousel-cta {
  justify-self: flex-start;
  padding: 0.85rem 1.9rem;
  border-radius: 999px;
  border: none;
  background: #ff5c00;
  color: #fff7f0;
  font-weight: 600;
  text-decoration: none;
  box-shadow: 0 16px 30px rgba(255, 92, 0, 0.35);
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.carousel-cta:hover {
  transform: translateY(-2px);
  box-shadow: 0 20px 36px rgba(255, 92, 0, 0.45);
}

.carousel-stage {
  position: relative;
  display: grid;
  grid-template-columns: auto 1fr auto;
  align-items: center;
  gap: 1rem;
}

.nav-btn {
  width: 48px;
  height: 48px;
  border-radius: 999px;
  border: none;
  background: rgba(15, 23, 42, 0.08);
  color: var(--color-navy);
  display: inline-flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: background 0.2s ease, transform 0.2s ease;
}

.nav-btn:hover {
  background: rgba(15, 23, 42, 0.18);
  transform: translateY(-2px);
}

.nav-btn svg {
  width: 20px;
  height: 20px;
}

.card-track {
  position: relative;
  overflow: hidden;
  height: clamp(320px, 38vw, 420px);
  --card-offset: clamp(150px, 18vw, 220px);
}

.carousel-card {
  position: absolute;
  top: 0;
  left: 50%;
  width: min(320px, 100%);
  border-radius: 28px;
  background: #ffffff;
  box-shadow: 0 15px 30px rgba(15, 23, 42, 0.12);
  padding: 1.75rem;
  display: grid;
  gap: 1rem;
  transition: transform 0.4s ease, opacity 0.4s ease, box-shadow 0.4s ease;
  opacity: 0;
  pointer-events: none;
  transform: translateX(-50%) scale(0.7);
}

.carousel-card.is-active {
  transform: translateX(-50%) scale(1);
  opacity: 1;
  pointer-events: auto;
  box-shadow: 0 24px 45px rgba(15, 23, 42, 0.16);
  z-index: 3;
}

.carousel-card.is-prev {
  opacity: 0.45;
  transform: translateX(calc(-50% - var(--card-offset))) scale(0.88);
  z-index: 2;
}

.carousel-card.is-next {
  opacity: 0.45;
  transform: translateX(calc(-50% + var(--card-offset))) scale(0.88);
  z-index: 2;
}

.carousel-card.is-rest {
  opacity: 0;
  transform: translateX(-50%) scale(0.7);
  z-index: 1;
}

.card-visual {
  border-radius: 20px;
  overflow: hidden;
  background: linear-gradient(135deg, rgba(236, 72, 153, 0.2), rgba(251, 146, 60, 0.2));
}

.card-visual img {
  width: 100%;
  height: 180px;
  object-fit: cover;
}

.card-body {
  display: grid;
  gap: 0.6rem;
}

.chip {
  display: inline-flex;
  align-items: center;
  padding: 0.2rem 0.75rem;
  border-radius: var(--radius-pill);
  background: rgba(236, 72, 153, 0.12);
  color: #9d174d;
  font-size: 0.8rem;
  font-weight: 600;
}

.card-body h3 {
  margin: 0;
  font-size: 1.3rem;
  color: var(--color-navy);
}

.card-body p {
  margin: 0;
  color: var(--color-text-muted);
  line-height: 1.6;
}

.card-link {
  justify-self: flex-start;
  font-weight: 600;
  color: var(--color-orange);
  text-decoration: none;
}

.card-link:hover {
  text-decoration: underline;
}

.carousel-controls {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 1rem;
}

.dots {
  display: inline-flex;
  gap: 0.5rem;
}

.dot {
  width: 28px;
  height: 4px;
  border-radius: 999px;
  border: none;
  background: rgba(148, 163, 184, 0.45);
  cursor: pointer;
  transition: background 0.2s ease, width 0.2s ease;
}

.dot.active {
  background: var(--color-orange);
  width: 42px;
}

.dot:focus-visible {
  outline: 2px solid var(--color-orange);
  outline-offset: 2px;
}

.play-btn {
  width: 40px;
  height: 40px;
  border-radius: 999px;
  border: none;
  background: rgba(15, 23, 42, 0.08);
  color: var(--color-navy);
  display: inline-flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: background 0.2s ease;
}

.play-btn:hover {
  background: rgba(15, 23, 42, 0.2);
}

.play-btn svg {
  width: 18px;
  height: 18px;
}

@media (max-width: 960px) {
  .carousel-head {
    grid-template-columns: 1fr;
  }

  .carousel-stage {
    grid-template-columns: 1fr;
  }

  .card-track {
    height: clamp(300px, 55vw, 380px);
    --card-offset: clamp(120px, 35vw, 160px);
  }
}

@media (max-width: 640px) {
  .solution-carousel {
    padding: 1.5rem;
  }

  .carousel-card {
    padding: 1.25rem;
  }
}
</style>
