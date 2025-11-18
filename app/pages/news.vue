<template>
  <section class="page">
    <header>
      <h1>新闻中心</h1>
      <p>最新动态、产品发布以及客户故事将陆续发布，敬请期待。</p>
    </header>
    <p>如需第一时间了解 Goodurs 的更新，请关注我们的公众号或联系顾问。</p>
  </section>
</template>

<style scoped>
.page {
  max-width: 760px;
  margin: 0 auto;
  display: grid;
  gap: 1.25rem;
}

header h1 {
  margin: 0 0 0.75rem;
  font-size: clamp(2rem, 5vw, 2.75rem);
  color: var(--color-navy);
}

header p {
  margin: 0;
  color: var(--color-text-muted);
  line-height: 1.6;
}
</style>
