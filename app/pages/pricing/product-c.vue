<template>
  <section class="pricing-page">
    <header class="page-hero">
      <h2>产品 C · 安全合规套件</h2>
      <p>覆盖数据安全、权限审计与合规监管，帮助企业满足行业要求。</p>
    </header>

    <section class="tiers">
      <article class="tier-card">
        <h3>安全基础包</h3>
        <p class="price">￥12,000 / 年</p>
        <ul>
          <li>统一身份认证</li>
          <li>登录与访问审计</li>
          <li>安全培训资源</li>
        </ul>
      </article>
      <article class="tier-card featured">
        <h3>合规加强包</h3>
        <p class="price">￥22,800 / 年</p>
        <ul>
          <li>数据脱敏策略</li>
          <li>应急响应流程</li>
          <li>定期安全评估</li>
        </ul>
      </article>
      <article class="tier-card">
        <h3>监管定制包</h3>
        <p class="price">定制报价</p>
        <ul>
          <li>行业合规落地</li>
          <li>安全团队共建</li>
          <li>7x24 监控响应</li>
        </ul>
      </article>
    </section>

    <section class="contact-cta">
      <h3>要通过合规审计？</h3>
      <p>我们提供全流程辅导与材料模板。</p>
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
  background: #17251c;
  color: var(--color-text-inverse);
  padding: 2.5rem;
  border-radius: 16px;
  box-shadow: 0 12px 32px rgba(23, 37, 28, 0.24);
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
  border: 2px solid #2bc66a;
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
  color: #2bc66a;
  text-decoration: none;
  font-weight: 600;
}
</style>
