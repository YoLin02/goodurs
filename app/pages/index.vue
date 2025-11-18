<script setup lang="ts">
import { onBeforeUnmount, onMounted, ref } from 'vue'

const testimonialSlides = [
  {
    image: 'https://dummyimage.com/640x360/e5e7eb/9ca3af&text=Case+Image+1',
    logo: 'https://dummyimage.com/160x48/f8fafc/1f2937&text=Brand+One',
    quote: '借助 Goodurs，企业可以在多团队协作中保持透明和高效，快速复制跨区域的交付经验。',
    link: '#'
  },
  {
    image: 'https://dummyimage.com/640x360/d1d5db/4b5563&text=Case+Image+2',
    logo: 'https://dummyimage.com/160x48/ffffff/0f172a&text=Brand+Two',
    quote: '我们通过 Goodurs 的内容运营体系让全球站点保持统一体验，并显著缩短上线周期。',
    link: '#'
  },
  {
    image: 'https://dummyimage.com/640x360/cbd5f5/0f172a&text=Case+Image+3',
    logo: 'https://dummyimage.com/160x48/fef3c7/92400e&text=Brand+Three',
    quote: 'Goodurs 的数据驱动方案帮助我们的运维团队在数周内完成跨地区整合，运营成本下降 30%。',
    link: '#'
  }
]

const activeSlide = ref(0)
let sliderTimer: number | null = null

const startSlider = () => {
  stopSlider()
  sliderTimer = window.setInterval(() => {
    activeSlide.value = (activeSlide.value + 1) % testimonialSlides.length
  }, 5000)
}

const stopSlider = () => {
  if (sliderTimer !== null) {
    clearInterval(sliderTimer)
    sliderTimer = null
  }
}

const setSlide = (index: number) => {
  activeSlide.value = index
  startSlider()
}

onMounted(startSlider)
onBeforeUnmount(stopSlider)
</script>

<template>
  <main class="landing">
    <section class="hero">
      <div class="hero-media" role="presentation">
        <img src="https://images.unsplash.com/photo-1517245386807-bb43f82c33c4?auto=format&fit=crop&w=1600&q=80" alt=""
          loading="lazy" />
        <div class="hero-overlay"></div>
      </div>
      <div class="hero-content">
        <p class="hero-tag">GOODURS CUSTOMER PLATFORM</p>
        <h1>Where go-to-market teams go to grow.</h1>
        <p>Unite marketing、销售与交付协作，在一个平台上快速复制成功经验。</p>
        <div class="hero-actions">
          <NuxtLink class="btn primary" to="/contact">立即预约</NuxtLink>
          <NuxtLink class="btn secondary" to="/pricing">获取方案</NuxtLink>
        </div>
      </div>
    </section>

    <div class="section-title">精选案例</div>

    <section class="cases-split-hero">
      <div class="cases-split-hero-inner">
        <!-- 左侧大图卡片（70%） -->
        <article class="case-card case-card-large">
          <div class="case-card-bg"
            style="background-image:url('https://img.alicdn.com/imgextra/i1/O1CN01Q9FxB71jVmeAIvSpT_!!6000000004554-2-tps-1422-641.png');">
          </div>

          <div class="case-card-overlay"></div>

          <div class="case-card-content">
            <img class="case-logo"
              src="https://img.alicdn.com/imgextra/i3/O1CN01QGNMnb25es3Gg00Zx_!!6000000007552-2-tps-440-132.png_.webp"
              alt="Genting" />

            <h2 class="case-title">
              阿里云的虚拟队列解决方案利用了人工智能，并集成了五个算法模块，可为云顶天城实现更高效的人群管理并动态减少游玩等待时间。
            </h2>

            <p class="case-tags">
              <span>酒店业</span>
              <span>企业/政府机构</span>
            </p>
          </div>
        </article>

        <!-- 右侧上下两张（30%，各 50% 高） -->
        <div class="case-side">
          <!-- 上：TVB -->
          <article class="case-card case-card-small">
            <div class="case-card-bg"
              style="background-image:url('https://img.alicdn.com/imgextra/i3/O1CN01YqJ6BX1eOqOzHyPp4_!!6000000003862-0-tps-840-170.jpg');">
            </div>

            <div class="case-card-overlay"></div>

            <div class="case-card-content">
              <img class="case-logo case-logo-small"
                src="https://img.alicdn.com/imgextra/i3/O1CN01b8fQdz1taUszwFIHQ_!!6000000005918-0-tps-2598-827.jpg_.webp"
                alt="TVB" />
              <h3 class="case-title-small">
                通过使用云技术，TVB为客户提供了世界一流的观看体验。
              </h3>
              <p class="case-tags">
                <span>科技</span>
              </p>
            </div>
          </article>

          <!-- 下：ABS-CBN -->
          <article class="case-card case-card-small">
            <div class="case-card-bg"
              style="background-image:url('https://img.alicdn.com/imgextra/i4/O1CN01jKJnUe2AAFU8QNKrv_!!6000000008162-0-tps-840-170.jpg');">
            </div>

            <div class="case-card-overlay"></div>

            <div class="case-card-content">
              <img class="case-logo case-logo-small"
                src="https://img.alicdn.com/imgextra/i4/O1CN01PtPfQx1s3EKaEfdRh_!!6000000005710-2-tps-144-56.png_.webp"
                alt="ABS-CBN" />
              <h3 class="case-title-small">
                借助阿里云，ABS-CBN可以在任何地方安全可靠地制作内容。
              </h3>
              <p class="case-tags">
                <span>媒体</span>
              </p>
            </div>
          </article>
        </div>
      </div>
    </section>
    <div class="customers-title-section">
      <h2 class="customers-title">
        全球超过135个国家的278,000名客户使用Nuclx发展他们的业务。
      </h2>
    </div>
    <div class="customers-section">
      <div class="customers-logos">
        <div class="logo-box">ebay</div>
        <div class="logo-box">DOORDASH</div>
        <div class="logo-box">reddit</div>
        <div class="logo-box">Tripadvisor</div>
        <div class="logo-box">eventbrite</div>
      </div>
    </div>


    <div class="banner-wrapper">
      <div class="banner">
        <div class="img"
          style="background-image:url('https://gw.alicdn.com/tfs/TB1hvujs21TBuNjy0FjXXajyXXa-2722-1190.png');"></div>

        <div class="right-mask"></div>

        <div class="left-box">
          <h2>了解阿里云如何支持阿里巴巴生态系统</h2>
          <p>
            <span>科技</span><span>电子商务</span><span>物流</span>
          </p>
        </div>

        <div class="right-box">
          <h1>阿里巴巴生态系统</h1>
          <p>了解阿里云如何为阿里巴巴生态系统提供技术和电商平台支持……</p>

          <main>
            <section
              style="background-image:url('https://img.alicdn.com/imgextra/i1/O1CN01BYpb9p1LYTzDjLeY6_!!6000000001311-2-tps-366-407.png');">
            </section>
            <section
              style="background-image:url('https://img.alicdn.com/imgextra/i1/O1CN01BYpb9p1LYTzDjLeY6_!!6000000001311-2-tps-366-407.png');">
            </section>
            <section
              style="background-image:url('https://img.alicdn.com/imgextra/i1/O1CN01BYpb9p1LYTzDjLeY6_!!6000000001311-2-tps-366-407.png');">
            </section>
          </main>
        </div>
      </div>
    </div>

    <div class="csol-section-wrapper">
      <div class="wf-animated-carousel-content">
        <!-- 顶部标题区域 -->
        <header class="wf-flexible-section-header">
          <div class="wf-flexible-section-header-top">
            <!-- 左侧 icon + 细线 -->
            <div class="wf-flexible-section-header-top_tagline-wrapper">
              <span class="wf-flexible-tagline cl-tagline cl-p -microheading -has-icon -icon-large -no-label"
                data-cl-theme="light">
                <img class="wf-flexible-tagline-icon"
                  src="https://web-hmleadnews-yolin.oss-cn-beijing.aliyuncs.com/Breeze_Icon.svg" alt="Breeze logo"
                  width="32" height="32" />
              </span>
              <div class="wf-flexible-section-header-top-line" aria-hidden="true"></div>
            </div>

            <!-- 右侧按钮 -->
            <a href="#" class="cl-button -tertiary-outline -medium -light wf-flexible-section-header-top_cta">
              Explore Breeze Agents
              <span class="visually-hidden">Built-in AI that work for you</span>
            </a>
          </div>

          <!-- 主标题 + 描述 -->
          <div class="wf-flexible-section-header-bottom -content-row">
            <h2 class="wf-flexible-section-header-heading cl-h2">
              内置 AI 代理，全天候为您工作。
            </h2>
            <p class="wf-flexible-section-header-description">
              纽科曙客服团队 是你随时在线的团队成员。
              他们可以解决超过 65% 的客户咨询，加快你的销售流程，并快速生成高质量内容。
            </p>
          </div>
        </header>

        <!-- 轮播区域 -->
        <div class="cl-carousel wf-animated-carousel-carousel" data-cl-theme="light"
          aria-label="Breeze Agents carousel">
          <div class="cl-carousel-viewport">
            <!-- 左右箭头 -->
            <div class="cl-carousel-controls">
              <button type="button" class="cl-round-button -light cl-carousel-controls-prev">
                <span class="visually-hidden">Previous slide</span>
                <svg class="cl-icon" aria-hidden="true">
                  <use href="#cl-icon-left"></use>
                </svg>
              </button>
              <button type="button" class="cl-round-button -light cl-carousel-controls-next">
                <span class="visually-hidden">Next slide</span>
                <svg class="cl-icon" aria-hidden="true">
                  <use href="#cl-icon-right"></use>
                </svg>
              </button>
            </div>

            <!-- 卡片轨道 -->
            <div class="cl-carousel-rail">
              <ul class="cl-carousel-train" role="list" aria-live="polite" aria-atomic="false">
                <!-- 卡片 1：Customer Agent -->
                <li class="cl-carousel-slide -left" role="group" aria-roledescription="slide" aria-label="1 of 3">
                  <article class="cl-card wf-animated-carousel-slide -light -container-01">
                    <img class="csol-image wf-animated-carousel-slide-image" data-cy="csol-base-image"
                      src="https://www.hubspot.com/hubfs/prospecting-agent-en@2x.png" alt="Customer Agent" width="640"
                      height="640" />
                    <h3 class="wf-animated-carousel-slide-title">
                      Customer Agent
                    </h3>
                    <p class="wf-animated-carousel-slide-description">
                      Resolve 65% of your customer inquiries automatically.
                    </p>
                    <a href="#" class="cl-textLink -light wf-animated-carousel-slide-link">
                      Learn More
                      <span class="visually-hidden">about Customer Agent</span>
                    </a>
                  </article>
                </li>

                <!-- 卡片 2：Prospecting Agent（中间主卡片） -->
                <li class="cl-carousel-slide -active" role="group" aria-roledescription="slide" aria-label="2 of 3">
                  <article class="cl-card wf-animated-carousel-slide -light -container-01">
                    <img class="csol-image wf-animated-carousel-slide-image" data-cy="csol-base-image"
                      src="https://www.hubspot.com/hubfs/prospecting-agent-en@2x.png" alt="Prospecting Agent"
                      width="640" height="640" />
                    <h3 class="wf-animated-carousel-slide-title">
                      Prospecting Agent
                    </h3>
                    <p class="wf-animated-carousel-slide-description">
                      Research, personalize, and execute sales outreach at scale —
                      instantly.
                    </p>
                    <a href="#" class="cl-textLink -light wf-animated-carousel-slide-link">
                      Learn More
                      <span class="visually-hidden">about Prospecting Agent</span>
                    </a>
                  </article>
                </li>

                <!-- 卡片 3：Data Agent -->
                <li class="cl-carousel-slide -right" role="group" aria-roledescription="slide" aria-label="3 of 3">
                  <article class="cl-card wf-animated-carousel-slide -light -container-01">
                    <span class="wf-animated-carousel-slide-badge cl-badge -rectangle -dot -beta">
                      <span class="cl-badge-dot"></span>
                      <span class="cl-badge-label">Beta</span>
                    </span>
                    <img class="csol-image wf-animated-carousel-slide-image" data-cy="csol-base-image"
                      src="https://www.hubspot.com/hubfs/prospecting-agent-en@2x.png" alt="Data Agent" width="640"
                      height="640" />
                    <h3 class="wf-animated-carousel-slide-title">
                      Data Agent
                    </h3>
                    <p class="wf-animated-carousel-slide-description">
                      Get instant answers to custom questions about your
                      customers.
                    </p>
                    <a href="#" class="cl-textLink -light wf-animated-carousel-slide-link">
                      Learn More
                      <span class="visually-hidden">about Data Agent</span>
                    </a>
                  </article>
                </li>
              </ul>
            </div>

            <!-- 底部暂停按钮 -->
            <footer class="cl-carousel-footer">
              <button type="button" class="cl-round-button -small cl-carousel-autoplay-toggle">
                <span class="visually-hidden">Pause carousel</span>
                <!-- 可以放 “||” 或 svg 图标 -->
              </button>
            </footer>
          </div>
        </div>
      </div>
    </div>

    <div class="case-section">
      <div class="case-header-row">
        <button class="case-tag">案例研究</button>

        <div class="case-line"></div>

        <button class="case-btn">查看所有案例研究</button>
      </div>

      <div class="case-content">
        <div class="case-title-01">
          为各种规模的企业带来卓越成果。
        </div>

        <div class="case-desc">
          使用 Nuclx 扩展您的业务。<br>
          证明就在于我们的客户成功。
        </div>
      </div>
    </div>
    <div class="testimonial-inner">
      <!-- Tabs -->
      <nav class="testimonial-tabs">
        <button class="testimonial-tab">Enterprise</button>
        <button class="testimonial-tab active">Mid-Sized Business</button>
        <button class="testimonial-tab">Small Business</button>
      </nav>

      <!-- Card -->
      <div class="testimonial-card">
        <div class="testimonial-main">
          <div class="testimonial-image">
            <!-- 换成你本地的图片路径即可 -->
            <img src="https://www.hubspot.com/hs-fs/hubfs/angel-FC.png?width=600&height=400&name=angel-FC.png"
              alt="Angel City FC fans" />
          </div>
          <div class="testimonial-text">
            <p class="quote">
              “HubSpot gave us the tools we needed to grow without losing the personal
              connection with our fans. Their support has been vital to our continued
              marketing success.”
            </p>
            <p class="author">Whitney Hallock</p>
            <p class="title">
              Director of Marketing &amp; Experience, Angel City FC
            </p>
            <a href="#" class="cta">Read full case study</a>
          </div>
        </div>

        <!-- Stats -->
        <div class="testimonial-stats">
          <div class="testimonial-stat">
            <div class="testimonial-stat-number">300%+</div>
            <div class="testimonial-stat-label">
              fan database growth in just 2 years
            </div>
          </div>
          <div class="testimonial-stat">
            <div class="testimonial-stat-number">~350</div>
            <div class="testimonial-stat-label">
              new fan sign-ups per week
            </div>
          </div>
          <div class="testimonial-stat">
            <div class="testimonial-stat-number">7</div>
            <div class="testimonial-stat-label">
              minutes average content engagement time
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
.landing {
  padding: 0 0 3rem;

  display: grid;
  gap: 3rem;
}

.hero {
  position: relative;
  min-height: calc(100vh - 88px);
  width: 100%;
  margin: 0;
  overflow: hidden;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  color: #fff;
}

.hero-media {
  position: absolute;
  inset: 0;
  margin-left: calc(50% - 50vw);
  margin-right: calc(50% - 50vw);
}

.hero-media img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.hero-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(120deg, rgba(0, 0, 0, 0.75), rgba(0, 0, 0, 0.35));
}

.hero-content {
  position: relative;
  z-index: 1;
  display: grid;
  gap: 1rem;
  padding: clamp(1.5rem, 5vw, 4rem);
  max-width: 900px;
}

.hero-tag {
  margin: 0;
  letter-spacing: 0.15em;
  font-size: 0.9rem;
  text-transform: uppercase;
  color: rgba(255, 255, 255, 0.7);
}

.hero h1 {
  margin: 0;
  font-size: clamp(2.2rem, 5vw, 3.6rem);
}

.hero p {
  margin: 0;
  line-height: 1.6;
}

.hero-actions {
  display: flex;
  gap: 1rem;
  justify-content: center;
  flex-wrap: wrap;
}

.btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 0.85rem 1.8rem;
  border-radius: 999px;
  text-decoration: none;
  color: inherit;
  border: 1px solid rgba(255, 255, 255, 0.5);
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.btn.primary {
  background: #ff7d20;
  border-color: #ff7d20;
}

.btn.secondary {
  background: transparent;
  border-color: #fff;
}

.btn:hover {
  transform: translateY(-2px);
}

.feature-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
  gap: 1.5rem;
}

.feature-grid article {
  background: #fff;
  padding: 1.5rem;
  border-radius: 20px;
  box-shadow: 0 12px 32px rgba(15, 23, 42, 0.12);
  border: 1px solid rgba(15, 23, 42, 0.08);
}

.feature-grid h3 {
  margin: 0 0 0.6rem;
  color: #0f172a;
}

.feature-grid p {
  margin: 0;
  color: #475569;
  line-height: 1.6;
}

.cta-section {
  background: #0f172a;
  color: #fff;
  border-radius: 24px;
  padding: 2rem;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  gap: 1rem;
  align-items: center;
}

.cta-section h2 {
  margin: 0 0 0.35rem;
}

.cta-section p {
  margin: 0;
  color: rgba(255, 255, 255, 0.8);
}

.section-title {
  text-align: center;
  font-size: 2.5rem;
  font-weight: 300;
  color: var(--color-navy, #0f172a);
  margin-top: -2rem;
  padding: 0 rem 0;
  background: #ffffff;
}

.cases-split-hero {
  padding: 24px 32px;
  background: #ffffff;
}

.cases-split-hero-inner {
  max-width: 1600px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 7fr 3fr;
  /* 左 70% 右 30% */
  grid-template-rows: 1fr 1fr;
  /* 右侧上下各 50% */
  height: 360px;
  /* 整块的统一高度 */
  gap: 0;
  /* 关键：去掉左右缝隙 */
  border-radius: 0;
  overflow: hidden;
  /* 圆角由父容器统一裁剪 */
  background: #000;
}

/* 左 70%，右 30% */
.case-card-large {
  grid-column: 1 / 2;
  grid-row: 1 / 3;
  /* 从第 1 行跨到第 3 行 => 占满上下 */
  height: 100%;
  /* 跟父容器等高 */
}

.case-side {
  grid-column: 2 / 3;
  grid-row: 1 / 3;
  display: grid;
  grid-template-rows: 1fr 1fr;
  /* 上下各 50% */
}

.case-card-small {
  flex: 1;
  /* 上下各占一半高度 */
}

/* 通用卡片基样式 */
.case-card {
  position: relative;
  border-radius: 0;
  overflow: hidden;
  cursor: pointer;
}

.case-card-bg {
  position: absolute;
  inset: 0;
  background-size: cover;
  background-position: center;
  transform: scale(1);
  transition: transform 0.4s ease;
}

/* 底部渐变遮罩提升文字可读性 */
.case-card-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(to top,
      rgba(0, 0, 0, 0.55),
      rgba(0, 0, 0, 0.15),
      rgba(0, 0, 0, 0));
}

.case-card-content {
  position: relative;
  z-index: 1;
  color: #fff;
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  height: 100%;
  padding: 32px 32px 28px;
}

.case-logo {
  max-width: 180px;
  margin-bottom: 48px;
}

.case-logo-small {
  max-width: 120px;
  margin-bottom: 12px;
}

.case-title {
  font-size: 17px;
  line-height: 1;
  font-weight: 500;
  margin-bottom: -20px;
}

.case-title-small {
  font-size: 16px;
  line-height: 1;
  font-weight: 500;
  margin-bottom: -10px;
}

.case-tags span {
  display: inline-block;
  margin-right: 10px;
  margin-top: -7px;
  padding: 4px 12px;
  border-radius: 0;
  border: 1px solid rgba(255, 255, 255, 0.7);
  font-size: 12px;
}

.case-tags {
  transform: translateY(29px);
  /* 所有卡片的标签都往上抬一点 */
}

/* 悬停放大效果（背景图缩放） */
.case-card:hover .case-card-bg {
  transform: scale(1.06);
}


.customers-title-section {
  width: 100%;

  /* 上下留白 */
  text-align: center;
  /* 文字居中 */
  background-color: #ffffff;
  /* 背景纯白，可按需调整 */
}

.customers-title {
  margin: 0 auto;
  max-width: 1080px;
  /* 控制行宽，看起来更像官网 */
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI",
    Roboto, "Helvetica Neue", Arial, sans-serif;
  font-size: 28px;
  /* 接近原图大小 */
  font-weight: 700;
  /* 粗体 */
  line-height: 1.2;
  color: #18212f;
  /* 深色标题文字 */
}

@media (max-width: 960px) {
  .cases-split-hero-inner {
    flex-direction: column;
  }

  .case-card-large,
  .case-side {
    flex: 1 1 auto;
    width: 100%;
  }

  .case-card-large {
    height: 260px;
  }
}

/* 外层整体区域 */
.customers-section {
  width: 100%;
  padding: 40px 0 60px;
  background: #ffffff;
  text-align: center;
}

/* Logo 容器：使用 flex 居中 + 等间隔 */
.customers-logos {
  display: flex;
  justify-content: center;
  gap: 40px;
  /* 五个 logo 的间距 */
  flex-wrap: wrap;
}

/* 单个占位图样式 */
.logo-box {
  width: 200px;
  height: 120px;
  background: #3367d6;
  /* 占位底色 */
  color: rgba(255, 255, 255, 0.85);
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 28px;
  font-weight: 600;
  border-radius: 8px;
  text-transform: uppercase;
  transition: transform 0.25s ease;
}

/* 悬停放大 */
.logo-box:hover {
  transform: scale(1.06);
}


/* Banner 外层容器：不全宽，居中 */
.banner-wrapper {
  width: 100%;
  max-width: 1600px;
  margin: 0 auto;
  display: block;
}

/* 整体 Banner */
.banner {
  position: relative;
  height: 560px;
  /* ★★★ 增加高度 */
  overflow: hidden;
  border-radius: 6px;
  font-family: "PingFang SC", -apple-system, BlinkMacSystemFont, "Microsoft Yahei", Arial, sans-serif;
}

/* 背景主图（铺满整个区域） */
.banner .img {
  position: absolute;
  inset: 0;
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  z-index: 1;
}

/* 右侧灰色半透明遮罩（覆盖图层和文字） */
.banner .right-mask {
  position: absolute;
  top: 0;
  right: 0;
  width: 40%;
  /* 更接近图二比例 */
  height: 100%;
  background: rgba(0, 0, 0, 0.55);
  /* ★★★ 加深灰色 */
  z-index: 3;
}

/* 左下文字 */
.banner .left-box {
  position: absolute;
  left: 70px;
  bottom: 30px;
  z-index: 5;
  color: #fff;
}

.banner .left-box h2 {
  font-size: 32px;
  margin-bottom: 20px;
  font-weight: 500;
}

.banner .left-box p span {
  display: inline-block;
  padding: 6px 18px;
  margin-right: 12px;
  border-radius: 20px;
  border: 1px solid rgba(255, 255, 255, 0.8);
  font-size: 15px;
}

/* 右侧内容（在遮罩上方） */
.banner .right-box {
  position: absolute;
  right: 0;
  top: 50px;
  /* ★★★ 随着高度增加调整垂直位置 */
  width: 34%;
  padding: 0 0px;
  z-index: 6;
  color: #fff;
}

.banner .right-box h1 {
  font-size: 36px;
  font-weight: 600;
  margin-bottom: 20px;
}

.banner .right-box p {
  font-size: 17px;
  line-height: 1.8;
  margin-bottom: 40px;
}

/* 右侧logo区图片位置调整 */
.banner .right-box main {
  display: flex;
  gap: 28px;
  margin-top: 180px;
}

.banner .right-box main section {
  display: block;
  width: 120px;
  height: 140px;
  background-size: cover;
  background-position: center;
  border-radius: 6px;
  box-shadow: 0 12px 28px rgba(0, 0, 0, 0.25);
  pointer-events: none;
}

/* ========== 基础布局 & 背景 ========== */
.wf-animated-carousel-section.-breeze.-light {
  padding: 80px 0;
  background: linear-gradient(90deg, #ffd4e3 0%, #ffd6c2 40%, #ffc9a4 100%);
  font-family: "HubSpot Sans", system-ui, -apple-system, BlinkMacSystemFont,
    "PingFang SC", "Microsoft Yahei", sans-serif;
  color: #213343;
}

.csol-section-wrapper {
  max-width: 1120px;
  margin: 0 auto;
}

/* ========== 顶部标题区域 ========== */
.wf-flexible-section-header {
  margin-bottom: 40px;
}

.wf-flexible-section-header-top {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 32px;
}

/* 左侧 logo + 细线 */
.wf-flexible-section-header-top_tagline-wrapper {
  display: flex;
  align-items: center;
  gap: 16px;
}

.wf-flexible-tagline {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 56px;
  height: 56px;
  border-radius: 18px;
  background: #fff;
  box-shadow: 0 16px 40px rgba(0, 0, 0, 0.12);
}

.wf-flexible-tagline-icon {
  width: 32px;
  height: 32px;
}

.wf-flexible-section-header-top-line {
  height: 1px;
  width: 220px;
  background: rgba(0, 0, 0, 0.08);
}

/* 右侧 Explore 按钮 */
.cl-button.-tertiary-outline.-medium.-light {
  border-radius: 999px;
  border: 1px solid #1f1f1f;
  background: rgba(255, 255, 255, 0.5);
  padding: 10px 22px;
  font-size: 14px;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.2s ease;
  color: #1f1f1f;
}

.cl-button.-tertiary-outline.-medium.-light:hover {
  background: #1f1f1f;
  color: #fff;
}

/* 标题 + 描述 */
.wf-flexible-section-header-bottom {
  display: flex;
  align-items: flex-start;
  justify-content: space-between;
  gap: 40px;
}

.wf-flexible-section-header-heading.cl-h2 {
  flex: 0 0 50%;
  font-family: "HubSpot Serif", "Times New Roman", serif;
  font-size: 40px;
  line-height: 1.2;
  font-weight: 500;
}

.wf-flexible-section-header-description {
  flex: 0 0 40%;
  font-size: 18px;
  line-height: 1.7;
  color: rgba(33, 51, 67, 0.9);
}

/* ========== 轮播整体 ========== */
.cl-carousel.wf-animated-carousel-carousel {
  margin-top: 56px;
  position: relative;
  min-height: 520px;
}

/* 轨道 & 布局 */
.cl-carousel-rail {
  max-width: 960px;
  margin: 48px auto 40px;
  padding: 0;
}

.cl-carousel-train {
  list-style: none;
  margin: 0;
  padding: 0;
  display: flex;
  justify-content: center;
  gap: 24px;
}

/* 每张 slide 占位宽度 */
.cl-carousel-slide {
  flex: 0 0 320px;
  display: flex;
  justify-content: center;
  transition: all 0.25s ease;
}

/* ========== 卡片样式 ========== */
.cl-card.wf-animated-carousel-slide {
  width: 100%;
  max-width: 320px;
  height: 460px;
  padding: 32px 28px 26px;
  border-radius: 28px;
  background: linear-gradient(180deg, #fff8f4 0%, #ffe7dd 100%);
  box-shadow: 0 22px 55px rgba(0, 0, 0, 0.12);
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  transition: all 0.25s ease;
}

/* 截图图片 */
.csol-image.wf-animated-carousel-slide-image {
  width: 100%;
  height: auto;
  border-radius: 18px;
  margin-bottom: 24px;
  box-shadow: 0 18px 40px rgba(0, 0, 0, 0.18);
}

/* 文案 */
.wf-animated-carousel-slide-title {
  font-size: 16px;
  font-weight: 600;
  margin-bottom: 6px;
  color: #213343;
}

.wf-animated-carousel-slide-description {
  font-size: 14px;
  line-height: 1.6;
  color: rgba(33, 51, 67, 0.85);
  margin-bottom: 18px;
}

/* Learn more 链接 */
.wf-animated-carousel-slide-link.cl-textLink.-light {
  font-size: 13px;
  font-weight: 500;
  color: #ff4f2b;
  text-decoration: none;
}

.wf-animated-carousel-slide-link.cl-textLink.-light:hover {
  text-decoration: underline;
}

/* Beta 小标签 */
.wf-animated-carousel-slide-badge.cl-badge.-rectangle.-dot.-beta {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 8px;
  padding: 4px 10px;
  border-radius: 999px;
  font-size: 11px;
  background: #f3e9ff;
  color: #9153ff;
}

/* 中间卡片高亮，两侧弱化 */
.cl-carousel-slide.-active .cl-card.wf-animated-carousel-slide {
  background: #ffffff;
  box-shadow: 0 26px 70px rgba(0, 0, 0, 0.2);
  transform: translateY(-6px) scale(1.02);
}

.cl-carousel-slide.-left .cl-card.wf-animated-carousel-slide,
.cl-carousel-slide.-right .cl-card.wf-animated-carousel-slide {
  opacity: 0.65;
  transform: scale(0.92);
}

/* ========== 左右箭头按钮 ========== */
.cl-carousel-controls {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 1200px;
  /* 与三张卡片宽度接近，按钮刚好在卡片外侧 */
  transform: translate(-50%, -50%);
  display: flex;
  justify-content: space-between;
  pointer-events: none;
}

.cl-carousel-controls .cl-round-button {
  pointer-events: auto;
}

.cl-round-button.-light {
  width: 44px;
  height: 44px;
  border-radius: 999px;
  border: none;
  background: #ffffff;
  box-shadow: 0 12px 28px rgba(0, 0, 0, 0.18);
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
}

.cl-round-button.-light svg {
  width: 18px;
  height: 18px;
  fill: #213343;
}

/* ========== 底部播放 / 暂停按钮 ========== */
.cl-carousel-footer {
  margin-top: 28px;
  display: flex;
  justify-content: center;
}

.cl-round-button.-small.cl-carousel-autoplay-toggle {
  width: 32px;
  height: 32px;
  border-radius: 999px;
  border: none;
  background: #ffffff;
  box-shadow: 0 6px 16px rgba(0, 0, 0, 0.18);
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
}

/* ========== 无障碍隐藏文本 ========== */
.visually-hidden {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border: 0;
}

/* ========== 简单响应式 ========== */
@media (max-width: 1024px) {
  .wf-flexible-section-header-bottom {
    flex-direction: column;
  }

  .wf-flexible-section-header-heading.cl-h2,
  .wf-flexible-section-header-description {
    flex: 1 1 auto;
  }

  .cl-carousel-rail {
    max-width: 100%;
    padding: 0 40px;
  }

  .cl-carousel-controls {
    width: calc(100% - 80px);
  }
}

@media (max-width: 768px) {
  .wf-flexible-section-header-top {
    flex-direction: column;
    align-items: flex-start;
    gap: 16px;
  }

  .wf-flexible-section-header-top-line {
    display: none;
  }

  .cl-carousel-rail {
    padding: 0 24px;
  }

  .cl-carousel-train {
    gap: 16px;
  }

  .cl-carousel-slide {
    flex: 0 0 80%;
  }

  .cl-carousel-controls {
    width: calc(100% - 48px);
  }
}

.case-section {
  width: 100%;
  max-width: 1280px;
  margin: -50px auto;
  padding: 20px;
  font-family: "Georgia", serif;
}

/* --- 顶部：标签、横线、按钮 --- */
.case-header-row {
  display: flex;
  align-items: center;
  width: 100%;
  margin-bottom: 40px;
}

.case-tag {
  padding: 10px 18px;
  background: white;
  border: 1px solid #ddd;
  font-size: 15px;
  border-radius: 8px;
  /* 变小圆角 */
  cursor: pointer;
}

.case-line {
  flex: 1;
  height: 0;
  border-bottom: 1px dashed #dcdcdc;
  margin: 0 20px;
}

.case-btn {
  padding: 10px 20px;
  border: 1px solid #222;
  background: white;
  font-size: 15px;
  border-radius: 8px;
  /* 小圆角按钮 */
  cursor: pointer;
}

/* --- 主内容：左右布局 --- */
.case-content {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  margin-top: 20px;
}

/* 左侧粗体标题 */
.case-title-01 {
  width: 45%;
  font-size: 46px;
  font-weight: 400;
  line-height: 1.2;
}

/* 右侧说明文字 */
.case-desc {
  width: 30%;
  font-size: 19px;
  line-height: 1.7;
  font-family: "Inter", sans-serif;
  color: #333;
}

* {
  box-sizing: border-box;
}

body {
  margin: 0;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue",
    Arial, sans-serif;
  background-color: #ffffff;
  color: #1f1f1f;
}

.testimonial-section {
  padding: 56px 16px 72px;
}

.testimonial-inner {
  max-width: 1260px;
  margin: 0 auto;
}

/* Tabs */
.testimonial-tabs {
  display: flex;
  justify-content: center;
  gap: 40px;
  font-size: 16px;
}

.testimonial-tab {
  position: relative;
  padding: 6px 0 10px;
  border: none;
  background: none;
  color: #6b7280;
  cursor: pointer;
  font: inherit;
  outline: none;
  transition: color 0.15s ease;
}

.testimonial-tab:hover {
  color: #111827;
}

.testimonial-tab.active {
  color: #111827;
  font-weight: 600;
}

.testimonial-tab.active::after {
  content: "";
  position: absolute;
  left: 0;
  right: 0;
  bottom: 0;
  height: 3px;
  background: #ff4800;
  border-radius: 999px;
}

/* Card */
.testimonial-card {
  margin-top: 28px;
  background: #ffffff;
  border-radius: 24px;
  border: 1px solid rgba(0, 0, 0, 0.06);
  box-shadow: 0 18px 40px rgba(15, 35, 52, 0.08);
  padding: 32px 40px 28px;
}

.testimonial-main {
  display: grid;
  grid-template-columns: minmax(0, 1.1fr) minmax(0, 1fr);
  gap: 32px;
  align-items: center;
}

.testimonial-image img {
  width: 100%;
  display: block;
  border-radius: 18px;
  object-fit: cover;
}

.testimonial-text .quote {
  font-size: 18px;
  line-height: 1.6;
  margin: 0 0 24px;
}

.testimonial-text .author {
  margin: 0 0 4px;
  font-weight: 600;
}

.testimonial-text .title {
  margin: 0 0 14px;
  font-size: 14px;
  color: #6b7280;
}

.testimonial-text .cta {
  font-size: 14px;
  color: #ff4800;
  text-decoration: none;
  border-bottom: 2px solid #ff4800;
  padding-bottom: 2px;
}

.testimonial-text .cta:hover {
  color: #c93700;
  border-color: #c93700;
}

/* Stats */
.testimonial-stats {
  margin-top: 28px;
  padding-top: 24px;
  border-top: 1px solid #e5e7eb;
  display: flex;
  justify-content: space-between;
  gap: 24px;
  text-align: center;
}

.testimonial-stat-number {
  font-size: 32px;
  font-weight: 600;
  margin-bottom: 6px;
}

.testimonial-stat-label {
  font-size: 14px;
  color: #6b7280;
}

/* 响应式 */
@media (max-width: 960px) {
  .testimonial-card {
    padding: 24px 20px 24px;
  }

  .testimonial-main {
    grid-template-columns: 1fr;
  }

  .testimonial-stats {
    flex-direction: column;
    align-items: center;
  }

  .testimonial-tabs {
    gap: 24px;
    font-size: 15px;
    flex-wrap: wrap;
  }
}
</style>
