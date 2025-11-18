<template>
  <section class="pricing-page">
    <header class="page-hero">
      <h2>产品 B · 数据与分析中台</h2>
      <p>汇聚多源数据，提供实时分析能力，帮助企业快速决策。</p>
    </header>

    <section class="tiers">
      <article class="tier-card">
        <h3>标准集成</h3>
        <p class="price">￥15,600 / 年</p>
        <ul>
          <li>10 个数据源接入</li>
          <li>BI 可视化看板</li>
          <li>基础数据仓库模型</li>
        </ul>
      </article>
      <article class="tier-card featured">
        <h3>专业集成</h3>
        <p class="price">￥28,800 / 年</p>
        <ul>
          <li>不限数据源接入</li>
          <li>高级权限管理</li>
          <li>机器学习预测模型</li>
        </ul>
      </article>
      <article class="tier-card">
        <h3>行业专属</h3>
        <p class="price">定制报价</p>
        <ul>
          <li>行业模板交付</li>
          <li>专家驻场辅导</li>
          <li>跨系统流程编排</li>
        </ul>
      </article>
    </section>

    <section class="contact-cta">
      <h3>想先试用？</h3>
      <p>联系我们获取行业 demo 与评估方案。</p>
      <NuxtLink to="/pricing" class="back-link">返回定价总览</NuxtLink>
    </section>
  </section>
</template>

<style scoped>
.pricing-page {
  display: grid;
  gap: 2.5rem;
}

.page-hero {
  background: #14212e;
  color: var(--color-text-inverse);
  padding: 2.5rem;
  border-radius: 16px;
  box-shadow: 0 12px 32px rgba(20, 33, 46, 0.24);
}

.page-hero h2 {
  margin: 0 0 1rem;
}

.tiers {
  display: grid;
  gap: 1.5rem;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
}

.tier-card {
  background: var(--color-surface);
  border-radius: 16px;
  padding: 2rem;
  box-shadow: var(--shadow-soft);
}

.tier-card.featured {
  border: 2px solid #0aa6ff;
}

.price {
  font-size: 1.5rem;
  font-weight: 700;
  margin: 0.75rem 0 1rem;
}

ul {
  margin: 0;
  padding-left: 1.2rem;
  color: var(--color-text-muted);
}

.contact-cta {
  background: var(--color-surface);
  padding: 2rem;
  border-radius: 16px;
  display: grid;
  gap: 0.5rem;
  box-shadow: var(--shadow-soft);
}

.back-link {
  justify-self: flex-start;
  color: #0aa6ff;
  text-decoration: none;
  font-weight: 600;
}
</style>
