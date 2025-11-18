<template>
  <section class="pricing-page">
    <header class="page-hero">
      <h2>产品 A · 智能化软件平台</h2>
      <p>支持按模块扩展的 SaaS 平台，助力企业快速上线数字化能力。</p>
    </header>

    <section class="tiers">
      <article class="tier-card">
        <h3>基础版</h3>
        <p class="price">￥9,800 / 年</p>
        <ul>
          <li>3 个业务模块</li>
          <li>团队权限管理</li>
          <li>标准化报表导出</li>
        </ul>
      </article>
      <article class="tier-card featured">
        <h3>成长版</h3>
        <p class="price">￥18,800 / 年</p>
        <ul>
          <li>全部业务模块</li>
          <li>API 集成支持</li>
          <li>优先级技术支持</li>
        </ul>
      </article>
      <article class="tier-card">
        <h3>旗舰版</h3>
        <p class="price">定制报价</p>
        <ul>
          <li>专属交付团队</li>
          <li>私有化部署</li>
          <li>定制数据治理</li>
        </ul>
      </article>
    </section>

    <section class="contact-cta">
      <h3>需要定制化方案？</h3>
      <p>留下需求，我们将在 24 小时内与您对接。</p>
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
  background: #101226;
  color: var(--color-text-inverse);
  padding: 2.5rem;
  border-radius: 16px;
  box-shadow: 0 12px 32px rgba(16, 18, 38, 0.24);
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
  border: 2px solid #3940ff;
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
  color: #3940ff;
  text-decoration: none;
  font-weight: 600;
}
</style>
