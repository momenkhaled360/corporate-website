<script setup lang="ts">
import { onMounted, onUnmounted, ref } from 'vue'

const services = [
  {
    number: '01',
    icon: '▦',
    title: 'الخرسانة الجاهزة',
    description:
      'توفير الخرسانة الجاهزة بمواصفات متنوعة لتلبية احتياجات المشروعات الإنشائية المختلفة.',
  },
  {
    number: '02',
    icon: '▥',
    title: 'منتجات البلك',
    description: 'توفير منتجات البلك المناسبة لأعمال البناء والتشييد بجودة تلبي متطلبات العملاء.',
  },
  {
    number: '03',
    icon: '◈',
    title: 'توريد للمشروعات',
    description:
      'توفير احتياجات مواقع العمل من المنتجات مع الاهتمام بالتنسيق والالتزام بمواعيد التوريد.',
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
  <section
    id="services"
    ref="sectionRef"
    class="services-section"
    :class="{ 'is-visible': isVisible }"
  >
    <div class="container">
      <div class="section-heading">
        <span class="section-label">خدماتنا</span>
        <h2>حلول متكاملة <span>لأعمال البناء</span></h2>
        <p>نقدم منتجات وخدمات تساعد على تلبية احتياجات المشروعات الإنشائية بمختلف أحجامها.</p>
      </div>

      <div class="services-grid">
        <article
          v-for="(service, index) in services"
          :key="service.number"
          class="service-card"
          :style="{ '--card-index': index }"
        >
          <div class="card-top">
            <span class="service-icon">{{ service.icon }}</span>
            <span class="service-number">{{ service.number }}</span>
          </div>

          <h3>{{ service.title }}</h3>

          <p>{{ service.description }}</p>

          <a href="#contact" class="service-link">
            اطلب الخدمة
            <span>←</span>
          </a>
        </article>
      </div>
    </div>
  </section>
</template>

<style scoped>
.services-section {
  padding: 110px 0;
  background: #f5f7fa;
  overflow: hidden;
}

.container {
  width: 94%;
  max-width: 1440px;
  margin: auto;
}

/* Section Heading Animation */
.section-heading {
  text-align: center;
  max-width: 700px;
  margin: 0 auto 55px;

  opacity: 0;
  transform: translateY(35px);
  transition:
    opacity 0.8s ease,
    transform 0.8s ease;
}

.is-visible .section-heading {
  opacity: 1;
  transform: translateY(0);
}

.section-label {
  display: inline-block;
  color: #c62828;
  font-size: 16px;
  font-weight: 800;
  margin-bottom: 5px;
}

.section-heading h2 {
  font-family: 'Alexandria', sans-serif;
  color: #174a7e;
  font-size: clamp(28px, 3vw, 40px);
  line-height: 1.6;
  margin: 15px 0;
}

.section-heading h2 span {
  color: #c62828;
}

.section-heading p {
  font-family: 'IBM Plex Sans Arabic', sans-serif;
  color: #64748b;
  font-size: 17px;
  line-height: 2;
}

/* Services Grid */
.services-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 25px;
}

/* Service Cards Animation */
.service-card {
  background: #ffffff;
  padding: 35px 30px;
  border-radius: 10px;
  border-bottom: 4px solid transparent;
  text-align: right;
  position: relative;
  overflow: hidden;

  opacity: 0;
  transform: translateY(50px);

  transition:
    opacity 0.7s ease,
    transform 0.7s ease,
    box-shadow 0.3s ease,
    border-color 0.3s ease;

  transition-delay: calc(var(--card-index) * 0.18s);
}

.is-visible .service-card {
  opacity: 1;
  transform: translateY(0);
}

/* Card Hover */
.service-card:hover {
  transform: translateY(-10px);
  border-bottom-color: #c62828;
  box-shadow: 0 15px 35px rgba(23, 74, 126, 0.12);
}

/* Card Top */
.card-top {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 30px;
}

.service-icon {
  width: 60px;
  height: 60px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: #fceeee;
  color: #c62828;
  font-size: 30px;
  border-radius: 10px;

  transition:
    transform 0.4s ease,
    background 0.3s ease,
    color 0.3s ease;
}

.service-card:hover .service-icon {
  transform: rotate(-8deg) scale(1.1);
  background: #c62828;
  color: #ffffff;
}

.service-number {
  font-family: 'Alexandria', sans-serif;
  font-size: 22px;
  font-weight: 800;
  color: #dce4ec;
}

.service-card h3 {
  font-family: 'Alexandria', sans-serif;
  font-size: 21px;
  color: #174a7e;
  margin: 0 0 15px;
}

.service-card p {
  font-family: 'IBM Plex Sans Arabic', sans-serif;
  color: #64748b;
  font-size: 15px;
  line-height: 2;
  min-height: 90px;
}

.service-link {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  margin-top: 20px;
  color: #174a7e;
  font-weight: 800;
  text-decoration: none;
  transition:
    color 0.3s ease,
    gap 0.3s ease;
}

.service-link:hover {
  color: #c62828;
  gap: 15px;
}

/* Responsive */
@media (max-width: 900px) {
  .services-grid {
    grid-template-columns: repeat(2, 1fr);
  }

  .services-section {
    padding: 80px 0;
  }
}

@media (max-width: 600px) {
  .services-grid {
    grid-template-columns: 1fr;
  }

  .service-card p {
    min-height: auto;
  }

  .section-heading p {
    font-size: 15px;
  }
}

/* Accessibility */
@media (prefers-reduced-motion: reduce) {
  .section-heading,
  .service-card {
    opacity: 1;
    transform: none;
    transition: none;
  }

  .service-icon {
    transition: none;
  }
}
</style>
