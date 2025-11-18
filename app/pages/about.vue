<template>
  <section class="page">
    <header>
      <h1>关于 Goodurs</h1>
      <p>我们致力于为企业提供全流程的数字化建站与增长服务。</p>
    </header>
    <div class="body">
      <p>
        团队结合品牌策略、用户体验、技术工程三大能力板块，帮助企业创建具备商业影响力的线上资产。当前
        产品矩阵覆盖 Shopify、Shopline、WordPress 以及企业级定制官网，满足不同规模与行业的业务场景。
      </p>
      <p>
        如果您需要了解更多合作模式，欢迎通过顶部导航中的“联系顾问”按钮与我们取得联系。
      </p>
    </div>
  </section>
</template>

<style scoped>
.page {
  display: grid;
  gap: 1.5rem;
  max-width: 760px;
  margin: 0 auto;
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

.body {
  display: grid;
  gap: 1rem;
  color: var(--color-text-primary);
  line-height: 1.75;
}
</style>
