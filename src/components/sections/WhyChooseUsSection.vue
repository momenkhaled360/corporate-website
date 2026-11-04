<script setup lang="ts">
const features = [
  {
    number: '01',
    title: 'جودة المنتجات',
    description: 'الاهتمام بجودة الخرسانة ومنتجات البلك ومطابقتها للمواصفات المطلوبة.',
    icon: '✓',
  },
  {
    number: '02',
    title: 'الالتزام بالمواعيد',
    description: 'الحرص على تنظيم عمليات التوريد والالتزام بالمواعيد المتفق عليها.',
    icon: '◷',
  },
  {
    number: '03',
    title: 'تلبية احتياجات العملاء',
    description: 'توفير حلول تناسب طبيعة المشروعات ومتطلبات كل عميل.',
    icon: '◇',
  },
  {
    number: '04',
    title: 'الثقة والمصداقية',
    description: 'بناء علاقات طويلة الأمد مع العملاء من خلال التعامل الواضح والموثوق.',
    icon: '◆',
  },
]
</script>

<template>
  <section class="why-section">
    <div class="container">
      <div class="why-heading">
        <span class="section-label">لماذا نحن؟</span>

        <h2>
          شريكك الموثوق
          <span>في أعمال البناء</span>
        </h2>

        <p>
          نؤمن أن نجاح أي مشروع يبدأ باختيار شريك يهتم بالجودة والالتزام وتلبية احتياجات العملاء.
        </p>

        <a href="#contact" class="why-button">ابدأ التعامل معنا</a>
      </div>

      <div class="features-grid">
        <article v-for="feature in features" :key="feature.number" class="feature-card">
          <div class="feature-top">
            <span class="feature-icon">{{ feature.icon }}</span>
            <span class="feature-number">{{ feature.number }}</span>
          </div>

          <h3>{{ feature.title }}</h3>
          <p>{{ feature.description }}</p>
        </article>
      </div>
    </div>
  </section>
</template>

<style scoped>
.why-section {
  padding: 110px 0;
  background: linear-gradient(145deg, #174a7e, #0f304f);
}

.container {
  width: 94%;
  max-width: 1440px;
  margin: auto;
  display: grid;
  grid-template-columns: 0.8fr 1.2fr;
  align-items: center;
  gap: 70px;
}

.why-heading {
  text-align: right;
}

.section-label {
  color: #ffb3b3;
  font-size: 16px;
  font-weight: 800;
}

.why-heading h2 {
  font-family: 'Alexandria', sans-serif;
  color: #ffffff;
  font-size: clamp(28px, 3vw, 40px);
  line-height: 1.7;
  margin: 18px 0;
}

.why-heading h2 span {
  display: block;
  color: #e53935;
}

.why-heading p {
  color: #e2eaf2;
  font-size: 16px;
  line-height: 2.1;
  margin-bottom: 30px;
}

.why-button {
  display: inline-block;
  padding: 13px 28px;
  background: #c62828;
  color: #ffffff;
  border-radius: 6px;
  text-decoration: none;
  font-weight: 800;
  transition: 0.3s ease;
}

.why-button:hover {
  background: #a91f1f;
  transform: translateY(-3px);
}

.features-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 20px;
}

.feature-card {
  padding: 28px;
  background: rgba(255, 255, 255, 0.08);
  border: 1px solid rgba(255, 255, 255, 0.12);
  border-radius: 10px;
  text-align: right;
  transition: 0.3s ease;
}

.feature-card:hover {
  background: rgba(255, 255, 255, 0.14);
  border-color: rgba(229, 57, 53, 0.5);
  transform: translateY(-5px);
}

.feature-top {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 25px;
}

.feature-icon {
  width: 48px;
  height: 48px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: #c62828;
  color: #ffffff;
  border-radius: 8px;
  font-size: 24px;
  font-weight: 800;
}

.feature-number {
  color: rgba(255, 255, 255, 0.3);
  font-family: 'Alexandria', sans-serif;
  font-size: 20px;
  font-weight: 800;
}

.feature-card h3 {
  font-family: 'Alexandria', sans-serif;
  color: #ffffff;
  font-size: 19px;
  margin: 0 0 12px;
}

.feature-card p {
  color: #d6e0e9;
  font-size: 14px;
  line-height: 2;
  margin: 0;
}

/* Responsive */
@media (max-width: 900px) {
  .container {
    grid-template-columns: 1fr;
    gap: 45px;
  }

  .why-section {
    padding: 80px 0;
  }
}

@media (max-width: 550px) {
  .features-grid {
    grid-template-columns: 1fr;
  }

  .feature-card {
    padding: 24px;
  }
}
</style>
