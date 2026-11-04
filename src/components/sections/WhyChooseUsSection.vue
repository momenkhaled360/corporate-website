<script setup lang="ts">
import { onMounted, onUnmounted, ref } from 'vue'

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

const sectionRef = ref<HTMLElement | null>(null)
const isVisible = ref(false)

let observer: IntersectionObserver | null = null

onMounted(() => {
  observer = new IntersectionObserver(
    (entries) => {
      if (entries[0]?.isIntersecting) {
        isVisible.value = true
        observer?.disconnect()
      }
    },
    {
      threshold: 0.15,
    },
  )

  if (sectionRef.value) {
    observer.observe(sectionRef.value)
  }
})

onUnmounted(() => {
  observer?.disconnect()
})
</script>

<template>
  <section ref="sectionRef" class="why-section" :class="{ 'is-visible': isVisible }">
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
        <article
          v-for="(feature, index) in features"
          :key="feature.number"
          class="feature-card"
          :style="{ '--feature-index': index }"
        >
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
  overflow: hidden;
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

/* Heading Animation */
.why-heading {
  text-align: right;

  opacity: 0;
  transform: translateX(45px);
  transition:
    opacity 0.8s ease,
    transform 0.8s ease;
}

.is-visible .why-heading {
  opacity: 1;
  transform: translateX(0);
}

.section-label {
  display: inline-block;
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

/* Button */
.why-button {
  display: inline-block;
  padding: 13px 28px;
  background: #c62828;
  color: #ffffff;
  border-radius: 6px;
  text-decoration: none;
  font-weight: 800;
  transition:
    background 0.3s ease,
    transform 0.3s ease,
    opacity 0.7s ease;

  opacity: 0;
  transform: translateY(20px);
}

.is-visible .why-button {
  opacity: 1;
  transform: translateY(0);
  transition-delay: 0.5s;
}

.why-button:hover {
  background: #a91f1f;
  transform: translateY(-3px);
}

/* Features Grid */
.features-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 20px;
}

/* Feature Card Animation */
.feature-card {
  padding: 28px;
  background: rgba(255, 255, 255, 0.08);
  border: 1px solid rgba(255, 255, 255, 0.12);
  border-radius: 10px;
  text-align: right;

  opacity: 0;
  transform: translateY(40px) scale(0.97);

  transition:
    opacity 0.7s ease,
    transform 0.7s ease,
    background 0.3s ease,
    border-color 0.3s ease,
    box-shadow 0.3s ease;

  transition-delay: calc(var(--feature-index) * 0.15s);
}

.is-visible .feature-card {
  opacity: 1;
  transform: translateY(0) scale(1);
}

.feature-card:hover {
  background: rgba(255, 255, 255, 0.14);
  border-color: rgba(229, 57, 53, 0.5);
  transform: translateY(-7px);
  box-shadow: 0 12px 30px rgba(0, 0, 0, 0.12);
}

/* Feature Top */
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

  opacity: 0;
  transform: scale(0.5) rotate(-15deg);
  transition:
    opacity 0.5s ease,
    transform 0.5s ease;
  transition-delay: calc(var(--feature-index) * 0.15s + 0.3s);
}

.is-visible .feature-icon {
  opacity: 1;
  transform: scale(1) rotate(0);
}

.feature-card:hover .feature-icon {
  transform: scale(1.12) rotate(5deg);
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

/* Accessibility */
@media (prefers-reduced-motion: reduce) {
  .why-heading,
  .why-button,
  .feature-card,
  .feature-icon {
    opacity: 1;
    transform: none;
    transition: none;
  }
}
</style>
