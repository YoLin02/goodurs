<script setup lang="ts">
import { reactive, ref } from 'vue'

const form = reactive({
  company: '',
  contact: '',
  email: '',
  phone: '',
  note: ''
})

const submitted = ref(false)

const handleSubmit = () => {
  submitted.value = true
}
</script>

<template>
  <section class="page">
    <div class="contact-info">
      <header>
        <h1>联系顾问</h1>
        <p>留下您的需求，我们将在 24 小时内安排顾问与您对接。</p>
      </header>
      <div class="body">
        <ul>
          <li>发送邮件至 <a href="mailto:hello@goodurs.com">hello@goodurs.com</a></li>
          <li>拨打企业热线：400-000-2025（工作日 09:00-18:00）</li>
          <li>提交详细项目资料后，可预约线上方案演示与报价评估。</li>
        </ul>
        <p>
          我们支持 Shopify、Shopline、WordPress 以及企业官网定制四大平台，项目团队包含产品经理、设计师、
          前端工程师与运营顾问，全程陪伴您的建站与增长计划。
        </p>
      </div>
    </div>

    <form class="form-card" @submit.prevent="handleSubmit">
      <h2>提交项目需求</h2>
      <p class="form-desc">请留下商务邮箱与联系电话，我们将回电提供一对一方案评估。</p>
      <label>
        公司 / 品牌
        <input v-model="form.company" type="text" placeholder="Goodurs Holding" required />
      </label>
      <label>
        联系人
        <input v-model="form.contact" type="text" placeholder="项目负责人" required />
      </label>
      <label>
        商务邮箱
        <input v-model="form.email" type="email" placeholder="you@example.com" required />
      </label>
      <label>
        联系电话
        <input v-model="form.phone" type="tel" placeholder="+86 138 0000 0000" required />
      </label>
      <label>
        备注说明
        <textarea v-model="form.note" rows="4" placeholder="请描述行业、预算区间或希望合作的具体模块……"></textarea>
      </label>
      <button type="submit">提交信息</button>
      <p v-if="submitted" class="form-feedback">已收到信息，顾问团队将尽快与您联系。</p>
    </form>
  </section>
</template>

<style scoped>
.page {
  display: grid;
  gap: 2rem;
  max-width: 1100px;
  margin: 0 auto;
  grid-template-columns: minmax(260px, 1fr) minmax(320px, 1fr);
  align-items: flex-start;
}

.contact-info header h1 {
  margin: 0 0 0.75rem;
  font-size: clamp(2rem, 5vw, 2.75rem);
  color: var(--color-navy);
}

.contact-info header p {
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

ul {
  margin: 0;
  padding-left: 1.25rem;
  display: grid;
  gap: 0.5rem;
}

a {
  color: var(--color-brand);
  text-decoration: none;
}

a:hover {
  text-decoration: underline;
}

.form-card {
  background: transparent;
  color: #111111;
  border-radius: 0;
  padding: 0;
  display: grid;
  gap: 1rem;
}

.form-card h2 {
  margin: 0;
  font-size: 1.6rem;
  color: #111111;
}

.form-desc {
  margin: 0;
  color: #333333;
  line-height: 1.6;
}

label {
  display: grid;
  gap: 0.35rem;
  font-size: 0.95rem;
  color: #111111;
}

input,
textarea {
  background: #ffffff;
  border: 1px solid #111111;
  border-radius: 8px;
  padding: 0.75rem 1rem;
  color: #111111;
  font: inherit;
}

input:focus,
textarea:focus {
  outline: 2px solid #111111;
  border-color: #111111;
}

button {
  margin-top: 0.5rem;
  padding: 0.9rem 1.6rem;
  border: none;
  border-radius: 999px;
  background: #111111;
  color: #ffffff;
  font-weight: 600;
  cursor: pointer;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

button:hover {
  transform: translateY(-2px);
  box-shadow: 0 10px 24px rgba(0, 0, 0, 0.25);
}

.form-feedback {
  margin: 0;
  color: #0f8b4c;
  font-size: 0.95rem;
}
</style>
