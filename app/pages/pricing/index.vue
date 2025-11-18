<template>
  <article class="pricing-landing">
    <header class="hero">
      <div class="hero-copy">
        <p class="eyebrow">全渠道建站服务</p>
        <h1>为企业定制的平台建站方案</h1>
        <p>
          我们结合 Shopfiy、Shopline、WordPress 与企业官方站四大平台能力，提供从需求分析、
          视觉设计到持续运营的端到端服务。
        </p>
        <NuxtLink class="hero-cta" to="/pricing/product-a">预约顾问了解方案</NuxtLink>
      </div>
      <div class="hero-meta">
        <div>
          <strong>4 套建站平台</strong>
          <span>覆盖跨境、电商、内容与综合门户</span>
        </div>
        <div>
          <strong>7×24</strong>
          <span>提供运维支持与运营培训</span>
        </div>
      </div>
    </header>

    <section class="platform-grid">
      <PlatformCard
        title="Shopify 建站"
        description="跨境电商优选，助力品牌快速验证市场。包含主题定制、支付对接与国际物流配置。"
        detail-route="/pricing/product-a"
        :features="[
          '精选 Shopify 模板 + 品牌化 UI',
          '多语言、多币种配置',
          '官方应用插件组合建议'
        ]"
      />

      <PlatformCard
        title="Shopline 建站"
        description="面向华语市场的本地化电商平台，整合营销插件加速增长。"
        detail-route="/pricing/product-b"
        :features="[
          '营销自动化与会员体系搭建',
          '社交媒体商城打通',
          '定期运营复盘与数据分析'
        ]"
      />

      <PlatformCard
        title="WordPress 建站"
        description="适合内容驱动型业务，支持灵活的内容模型与 SEO 深度优化。"
        detail-route="/pricing/product-c"
        :features="[
          '企业级安全加固与备份策略',
          '自定义内容模板与区块',
          '第三方系统 API 集成'
        ]"
      />

      <PlatformCard
        title="企业官网定制"
        description="面向集团级组织的品牌官网，覆盖品牌故事、业务矩阵与招商合作入口。"
        detail-route="/pricing/product-d"
        :features="[
          '从零搭建信息架构与视觉体系',
          '多终端响应式适配',
          'CDN 加速与性能调优'
        ]"
      />
    </section>
  </article>
</template>

<style scoped>
.pricing-landing {
  display: grid;
  gap: 3rem;
}

.hero {
  display: grid;
  gap: 2rem;
  padding: 3rem;
  border-radius: 20px;
  background: radial-gradient(circle at 20% 20%, rgba(14, 165, 233, 0.16), transparent 50%),
    radial-gradient(circle at 80% 10%, rgba(59, 130, 246, 0.25), transparent 55%),
    var(--color-navy);
  color: var(--color-text-inverse);
  box-shadow: 0 24px 40px rgba(10, 26, 58, 0.25);
}

.hero-copy {
  max-width: 520px;
  display: grid;
  gap: 1rem;
}

.eyebrow {
  font-size: 0.875rem;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: rgba(148, 163, 184, 0.85);
}

.hero h1 {
  margin: 0;
  font-size: clamp(2.2rem, 4vw, 3rem);
}

.hero p {
  margin: 0;
  line-height: 1.6;
}

.hero-cta {
  justify-self: flex-start;
  padding: 0.85rem 1.8rem;
  border-radius: 999px;
  background: var(--color-brand);
  color: var(--color-navy);
  text-decoration: none;
  font-weight: 700;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
  box-shadow: 0 16px 30px rgba(14, 165, 233, 0.35);
}

.hero-cta:hover {
  transform: translateY(-3px);
  box-shadow: 0 20px 34px rgba(14, 165, 233, 0.45);
}

.hero-meta {
  display: grid;
  gap: 1rem;
  grid-auto-flow: column;
  grid-auto-columns: minmax(0, 1fr);
}

.hero-meta div {
  padding: 1.5rem;
  border-radius: 16px;
  background: rgba(15, 23, 42, 0.6);
  border: 1px solid rgba(148, 163, 184, 0.25);
  display: grid;
  gap: 0.35rem;
}

.hero-meta strong {
  font-size: 1.35rem;
}

.hero-meta span {
  color: rgba(226, 232, 240, 0.75);
}

.platform-grid {
  display: grid;
  gap: 1.8rem;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
}

@media (max-width: 960px) {
  .hero {
    padding: 2.5rem;
  }

  .hero-meta {
    grid-auto-flow: row;
  }
}
</style>
