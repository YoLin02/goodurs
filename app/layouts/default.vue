<template>
  <div class="page-shell">
    <header class="page-header">
      <NuxtLink to="/" class="brand">
        <span class="brand-mark" aria-hidden="true">G</span>
        <span class="brand-word">Goodurs</span>
      </NuxtLink>
      <nav class="primary-nav" aria-label="主导航">
        <NuxtLink class="nav-link" to="/">首页</NuxtLink>
        <div class="nav-item has-dropdown">
          <NuxtLink class="nav-link nav-trigger" to="/pricing" aria-haspopup="true">
            产品
            <span class="chevron" aria-hidden="true">
              <svg width="12" height="12" viewBox="0 0 24 24" fill="none" aria-hidden="true">
                <path d="M6 9l6 6 6-6" stroke="currentColor" stroke-width="2" stroke-linecap="round"
                  stroke-linejoin="round" />
              </svg>
            </span>
          </NuxtLink>
          <div class="dropdown" role="menu">
            <NuxtLink class="dropdown-link" to="/pricing/product-b">Shopline 建站</NuxtLink>
            <NuxtLink class="dropdown-link" to="/pricing/product-c">WordPress 建站</NuxtLink>
            <NuxtLink class="dropdown-link" to="/pricing/product-d">企业官网定制</NuxtLink>
            <NuxtLink class="dropdown-link" to="/pricing/product-a">Shopify 建站</NuxtLink>
          </div>
        </div>
        <NuxtLink class="nav-link" to="/partners">合作伙伴</NuxtLink>
        <NuxtLink class="nav-link" to="/news">新闻中心</NuxtLink>
        <NuxtLink class="nav-link" to="/about">关于我们</NuxtLink>
      </nav>
      <NuxtLink class="cta" to="/contact">联系顾问</NuxtLink>
    </header>
    <main class="page-content">
      <slot />
    </main>
    <footer class="page-footer">
      <small>&copy; {{ currentYear }} Goodurs. 保留所有权利。</small>
    </footer>
  </div>
</template>

<script setup lang="ts">
const currentYear = new Date().getFullYear()
</script>

<style scoped>
.page-shell {
  min-height: 100vh;
  display: grid;
  grid-template-rows: auto 1fr auto;
  font-family: var(--font-family-base);
  background: var(--color-bg-body);
  color: var(--color-text-primary);
}

.page-header {
  display: flex;
  align-items: center;
  gap: 1.5rem;
  justify-content: space-between;
  padding: 1rem 2rem;
  background: #ffffff;
  color: var(--color-text-primary);
  box-shadow: 0 2px 12px rgba(15, 23, 42, 0.08);
  position: sticky;
  top: 0;
  z-index: 30;
}

.brand {
  display: inline-flex;
  align-items: center;
  gap: 0.75rem;
  font-size: 1.25rem;
  margin: 0;
  color: var(--color-text-primary);
  text-decoration: none;
  font-weight: 700;
}

.brand-mark {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 2.25rem;
  height: 2.25rem;
  border-radius: 999px;
  background: linear-gradient(135deg, var(--color-brand), #3b82f6);
  font-weight: 800;
}

.brand-word {
  letter-spacing: 0.02em;
}

.primary-nav {
  flex: 1;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 1.8rem;
}

.nav-link {
  position: relative;
  display: inline-flex;
  align-items: center;
  gap: 0.35rem;
  color: var(--color-text-primary);
  text-decoration: none;
  font-weight: 600;
  padding: 0.25rem 0;
}

.nav-link.router-link-active::after {
  content: '';
  position: absolute;
  left: 0;
  right: 0;
  bottom: -0.35rem;
  height: 2px;
  background: var(--color-orange);
}

.nav-item {
  position: relative;
}

.chevron {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 1rem;
  height: 1rem;
  opacity: 0.8;
  transition: transform 0.2s ease;
}

.has-dropdown:hover .chevron,
.has-dropdown:focus-within .chevron {
  transform: rotate(180deg);
}

.dropdown {
  position: absolute;
  left: 0;
  top: calc(100% + 0.75rem);
  min-width: 220px;
  padding: 1rem 0.75rem;
  background: #ffffff;
  border-radius: 16px;
  box-shadow: 0 18px 36px rgba(15, 23, 42, 0.15);
  display: grid;
  gap: 0.25rem;
  opacity: 0;
  pointer-events: none;
  transform: translateY(6px);
  transition: opacity 0.2s ease, transform 0.2s ease;
  z-index: 20;
}

.has-dropdown:hover .dropdown,
.has-dropdown:focus-within .dropdown {
  opacity: 1;
  pointer-events: auto;
  transform: translateY(0);
}

.dropdown::before {
  content: '';
  position: absolute;
  top: -0.6rem;
  left: 1.5rem;
  width: 1rem;
  height: 1rem;
  background: inherit;
  transform: rotate(45deg);
  border-radius: 3px;
  z-index: -1;
}

.dropdown-link {
  display: block;
  padding: 0.6rem 0.75rem;
  border-radius: 10px;
  color: var(--color-text-primary);
  text-decoration: none;
  font-weight: 500;
  transition: background 0.2s ease;
}

.dropdown-link:hover,
.dropdown-link:focus-visible {
  background: rgba(14, 165, 233, 0.18);
}

.dropdown-link.router-link-active {
  background: rgba(14, 165, 233, 0.15);
}

.cta {
  padding: 0.65rem 1.4rem;
  border-radius: var(--radius-pill);
  background: var(--color-orange);
  color: #ffffff;
  text-decoration: none;
  font-weight: 600;
  transition: transform 0.2s ease, background 0.2s ease, color 0.2s ease;
}

.cta:hover {
  transform: translateY(-2px);
  background: #ff7d20;
  color: #ffffff;
}

.page-content {
  padding: 0 0 2rem;
}

.page-footer {
  padding: 1rem 2rem;
  background: var(--color-navy);
  color: var(--color-text-inverse);
  text-align: center;
}

@media (max-width: 960px) {
  .page-header {
    flex-direction: column;
    align-items: flex-start;
  }

  .primary-nav {
    width: 100%;
    justify-content: flex-start;
    flex-wrap: wrap;
    gap: 1rem;
  }

  .cta {
    align-self: flex-start;
  }
}
</style>
