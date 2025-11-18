<template>
  <section
    class="spotlight"
    @mouseenter="pauseAuto"
    @mouseleave="startAuto"
  >
    <div class="spotlight-panel">
      <div class="brand-block">
        <img :src="activeItem.logo" :alt="`${activeItem.name} 品牌标识`" loading="lazy" />
        <span class="brand-name">{{ activeItem.name }}</span>
      </div>
      <div class="quote-block">
        <span class="quote-mark left">&ldquo;</span>
        <p>{{ activeItem.quote }}</p>
        <span class="quote-mark right">&rdquo;</span>
        <NuxtLink :to="activeItem.link" class="details-link">了解详情</NuxtLink>
      </div>
    </div>

    <div class="spotlight-dots" role="tablist">
      <button
        v-for="(item, index) in items"
        :key="item.name"
        type="button"
        :aria-label="`切换至 ${item.name} 合作故事`"
        :aria-selected="index === activeIndex"
        :class="['dot', { active: index === activeIndex }]"
        role="tab"
        @click="selectItem(index)"
      />
    </div>
  </section>
</template>

<script setup lang="ts">
import { computed, onBeforeUnmount, onMounted, ref, watch } from 'vue'

type SpotlightItem = {
  name: string
  logo: string
  quote: string
  link: string
}

const props = withDefaults(
  defineProps<{
    items: SpotlightItem[]
    interval?: number
  }>(),
  {
    interval: 6000
  }
)

const activeIndex = ref(0)
const timer = ref<number | null>(null)
const defaultItem: SpotlightItem = {
  name: '即将上线',
  logo: '',
  quote: '敬请期待更多合作故事。',
  link: '/contact'
}

const stopAuto = () => {
  if (timer.value !== null) {
    clearInterval(timer.value)
    timer.value = null
  }
}

const startAuto = () => {
  stopAuto()
  if (props.items.length > 1) {
    timer.value = window.setInterval(() => {
      activeIndex.value = (activeIndex.value + 1) % props.items.length
    }, props.interval)
  }
}

const pauseAuto = () => stopAuto()

const selectItem = (index: number) => {
  activeIndex.value = index
  startAuto()
}

const activeItem = computed<SpotlightItem>(
  () => props.items[activeIndex.value] ?? props.items[0] ?? defaultItem
)

onMounted(() => {
  if (props.items.length > 1) startAuto()
})
onBeforeUnmount(stopAuto)

watch(
  () => props.items,
  () => {
    activeIndex.value = 0
    if (props.items.length > 1) startAuto()
  },
  { deep: true }
)
</script>

<style scoped>
.spotlight {
  background: #f7f8fb;
  border-radius: 24px;
  padding: clamp(1.5rem, 4vw, 2.5rem);
  display: grid;
  gap: 1.5rem;
  box-shadow: 0 12px 30px rgba(15, 23, 42, 0.08);
}

.spotlight-panel {
  display: grid;
  gap: clamp(1.5rem, 4vw, 3rem);
  grid-template-columns: minmax(0, 240px) minmax(0, 1fr);
  align-items: center;
}

.brand-block {
  display: grid;
  justify-items: center;
  gap: 1rem;
  text-align: center;
}

.brand-block img {
  width: clamp(140px, 18vw, 200px);
  height: auto;
  object-fit: contain;
}

.brand-name {
  font-weight: 600;
  color: var(--color-text-primary);
}

.quote-block {
  position: relative;
  background: #ffffff;
  border-radius: 20px;
  padding: clamp(1.5rem, 3vw, 2.5rem);
  box-shadow: inset 0 0 0 1px rgba(15, 23, 42, 0.05);
  display: grid;
  gap: 1.25rem;
}

.quote-mark {
  position: absolute;
  font-size: clamp(2.5rem, 5vw, 3.5rem);
  line-height: 1;
  color: rgba(148, 163, 184, 0.6);
  font-family: 'Georgia', serif;
}

.quote-mark.left {
  top: 1rem;
  left: 1.5rem;
}

.quote-mark.right {
  bottom: 1rem;
  right: 1.5rem;
}

.quote-block p {
  margin: 0;
  color: var(--color-text-primary);
  font-size: clamp(1rem, 2vw, 1.2rem);
  line-height: 1.7;
}

.details-link {
  justify-self: flex-start;
  padding: 0.5rem 1.6rem;
  border-radius: var(--radius-pill);
  border: 1px solid var(--color-orange);
  color: var(--color-orange);
  font-weight: 600;
  text-decoration: none;
  transition: background 0.2s ease, color 0.2s ease;
}

.details-link:hover {
  background: var(--color-orange);
  color: var(--color-navy);
}

.spotlight-dots {
  display: flex;
  gap: 0.5rem;
  justify-content: flex-end;
}

.dot {
  width: 34px;
  height: 4px;
  border-radius: 999px;
  border: none;
  background: rgba(148, 163, 184, 0.4);
  cursor: pointer;
  transition: background 0.2s ease, width 0.2s ease;
}

.dot.active {
  background: var(--color-orange);
  width: 48px;
}

.dot:focus-visible {
  outline: 2px solid var(--color-orange);
  outline-offset: 2px;
}

@media (max-width: 768px) {
  .spotlight-panel {
    grid-template-columns: 1fr;
    justify-items: center;
    text-align: center;
  }

  .quote-block {
    text-align: left;
  }

  .spotlight-dots {
    justify-content: center;
  }
}
</style>
