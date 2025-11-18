<template>
  <section class="pricing-page">
    <header class="page-hero">
      <h2>产品 D · 硬件一体化方案</h2>
      <p>从设备采购、安装到运维托管的一站式服务，适配多行业场景。</p>
    </header>

    <section class="tiers">
      <article class="tier-card">
        <h3>标准部署</h3>
        <p class="price">￥38,000 / 套</p>
        <ul>
          <li>核心硬件设备</li>
          <li>现场安装调试</li>
          <li>一年质保服务</li>
        </ul>
      </article>
      <article class="tier-card featured">
        <h3>扩展部署</h3>
        <p class="price">￥55,000 / 套</p>
        <ul>
          <li>扩展模块与配件</li>
          <li>远程监控平台</li>
          <li>三年维保服务</li>
        </ul>
      </article>
      <article class="tier-card">
        <h3>定制部署</h3>
        <p class="price">定制报价</p>
        <ul>
          <li>多区域统一运维</li>
          <li>专属安装团队</li>
          <li>全生命周期托管</li>
        </ul>
      </article>
    </section>

    <section class="contact-cta">
      <h3>需要现场勘测？</h3>
      <p>提交部署地址，专家团队将提供免费预评估。</p>
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
  background: #2c1b2d;
  color: var(--color-text-inverse);
  padding: 2.5rem;
  border-radius: 16px;
  box-shadow: 0 12px 32px rgba(44, 27, 45, 0.24);
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
  border: 2px solid #d16bff;
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
  color: #d16bff;
  text-decoration: none;
  font-weight: 600;
}
</style>
