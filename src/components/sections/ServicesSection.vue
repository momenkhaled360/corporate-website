<script setup lang="ts">
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
</script>

<template>
  <section id="services" class="services-section">
    <div class="container">
      <div class="section-heading">
        <span class="section-label">خدماتنا</span>
        <h2>حلول متكاملة <span>لأعمال البناء</span></h2>
        <p>نقدم منتجات وخدمات تساعد على تلبية احتياجات المشروعات الإنشائية بمختلف أحجامها.</p>
      </div>

      <div class="services-grid">
        <article v-for="service in services" :key="service.number" class="service-card">
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
  background: #e9eef3;
}

.container {
  width: 94%;
  max-width: 1440px;
  margin: auto;
}

.section-heading {
  text-align: center;
  max-width: 700px;
  margin: 0 auto 55px;
}

.section-label {
  color: #f28c28;
  font-size: 16px;
  font-weight: 800;
}

.section-heading h2 {
  font-family: 'Alexandria', sans-serif;
  color: #23476a;
  font-size: clamp(28px, 3vw, 40px);
  line-height: 1.6;
  margin: 15px 0;
}

.section-heading h2 span {
  color: #f28c28;
}

.section-heading p {
  font-family: 'IBM Plex Sans Arabic', sans-serif;
  color: #64748b;
  font-size: 17px;
  line-height: 2;
}

.services-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 25px;
}

.service-card {
  background: #ffffff;
  padding: 35px 30px;
  border-radius: 10px;
  border-bottom: 4px solid transparent;
  transition: all 0.3s ease;
  text-align: right;
}

.service-card:hover {
  transform: translateY(-8px);
  border-bottom-color: #f28c28;
  box-shadow: 0 15px 35px rgba(35, 71, 106, 0.1);
}

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
  background: #fff3e6;
  color: #f28c28;
  font-size: 30px;
  border-radius: 10px;
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
  color: #23476a;
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
  color: #23476a;
  font-weight: 800;
  text-decoration: none;
  transition: color 0.3s ease;
}

.service-link:hover {
  color: #f28c28;
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
</style>
