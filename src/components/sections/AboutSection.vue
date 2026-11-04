<script setup lang="ts">
import { onMounted, onUnmounted, ref } from 'vue'

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
      threshold: 0.2,
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
  <section id="about" ref="sectionRef" class="about-section" :class="{ 'is-visible': isVisible }">
    <div class="container">
      <div class="about-content">
        <span class="section-label">من نحن</span>

        <h2>
          خبرة في البناء...
          <span>وثقة في كل مشروع</span>
        </h2>

        <p class="about-paragraph first-paragraph">
          شركة المروج العربية للخرسانة الجاهزة والبلك، نعمل على تقديم حلول متكاملة في مجال الخرسانة
          الجاهزة ومنتجات البلك، مع الالتزام بأعلى معايير الجودة والدقة في التنفيذ.
        </p>

        <p class="about-paragraph second-paragraph">
          نسعى إلى أن نكون شريكاً موثوقاً لعملائنا من خلال توفير منتجات عالية الجودة، والالتزام
          بمواعيد التسليم، وتلبية احتياجات مختلف المشروعات.
        </p>

        <a href="#contact" class="about-button">تواصل معنا</a>
      </div>

      <div class="about-visual">
        <div class="visual-card">
          <span class="visual-number">01</span>
          <h3>الجودة أولويتنا</h3>
          <p>نهتم بأدق التفاصيل لضمان تقديم منتجات تلبي تطلعات عملائنا.</p>
        </div>

        <div class="visual-bottom">
          <span>المروج العربية</span>
          <span>نبني بثقة</span>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.about-section {
  padding: 110px 0;
  background: #ffffff;
  overflow: hidden;
}

.container {
  width: 94%;
  max-width: 1440px;
  margin: auto;
  display: grid;
  grid-template-columns: 1fr 0.9fr;
  align-items: center;
  gap: 80px;
}

/* About Content */
.about-content {
  text-align: right;
}

.section-label,
.about-content h2,
.about-paragraph,
.about-button {
  opacity: 0;
  transform: translateX(45px);
  transition:
    opacity 0.8s ease,
    transform 0.8s ease;
}

.is-visible .section-label {
  opacity: 1;
  transform: translateX(0);
  transition-delay: 0.1s;
}

.is-visible .about-content h2 {
  opacity: 1;
  transform: translateX(0);
  transition-delay: 0.25s;
}

.is-visible .first-paragraph {
  opacity: 1;
  transform: translateX(0);
  transition-delay: 0.4s;
}

.is-visible .second-paragraph {
  opacity: 1;
  transform: translateX(0);
  transition-delay: 0.55s;
}

.is-visible .about-button {
  opacity: 1;
  transform: translateX(0);
  transition-delay: 0.7s;
}

.section-label {
  display: inline-block;
  color: #c62828;
  font-size: 16px;
  font-weight: 800;
  margin-bottom: 18px;
}

.about-content h2 {
  font-family: 'Alexandria', sans-serif;
  font-size: clamp(28px, 3vw, 42px);
  line-height: 1.6;
  color: #174a7e;
  margin: 0 0 25px;
  font-weight: 800;
}

.about-content h2 span {
  display: block;
  color: #c62828;
}

.about-content p {
  font-family: 'IBM Plex Sans Arabic', sans-serif;
  color: #64748b;
  font-size: 17px;
  line-height: 2.1;
  margin-bottom: 15px;
}

.about-button {
  display: inline-block;
  margin-top: 20px;
  padding: 13px 30px;
  background: #174a7e;
  color: #ffffff;
  border-radius: 6px;
  text-decoration: none;
  font-weight: 700;
  transition:
    opacity 0.8s ease,
    transform 0.8s ease,
    background 0.3s ease;
}

.about-button:hover {
  background: #c62828;
  transform: translateY(-3px);
}

/* Visual Card Animation */
.about-visual {
  min-height: 390px;
  background: linear-gradient(145deg, #174a7e, #0f304f);
  border-radius: 12px;
  padding: 45px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  position: relative;
  overflow: hidden;

  opacity: 0;
  transform: translateX(-60px);
  transition:
    opacity 1s ease,
    transform 1s ease;
  transition-delay: 0.2s;
}

.is-visible .about-visual {
  opacity: 1;
  transform: translateX(0);
}

.about-visual::before {
  content: '';
  position: absolute;
  width: 280px;
  height: 280px;
  border: 45px solid rgba(255, 255, 255, 0.06);
  border-radius: 50%;
  top: -100px;
  left: -80px;
  animation: circleFloat 7s ease-in-out infinite alternate;
}

.visual-card {
  position: relative;
  z-index: 1;
  color: #ffffff;
}

.visual-number {
  font-family: 'Alexandria', sans-serif;
  font-size: 70px;
  font-weight: 900;
  color: #e53935;
  display: block;
  margin-bottom: 15px;

  opacity: 0;
  transform: translateY(20px);
  transition: all 0.7s ease;
  transition-delay: 0.8s;
}

.is-visible .visual-number {
  opacity: 1;
  transform: translateY(0);
}

.visual-card h3 {
  font-family: 'Alexandria', sans-serif;
  font-size: 25px;
  margin: 0 0 15px;

  opacity: 0;
  transform: translateY(20px);
  transition: all 0.7s ease;
  transition-delay: 0.95s;
}

.is-visible .visual-card h3 {
  opacity: 1;
  transform: translateY(0);
}

.visual-card p {
  color: #e2eaf2;
  font-size: 16px;
  line-height: 2;
  max-width: 400px;

  opacity: 0;
  transform: translateY(20px);
  transition: all 0.7s ease;
  transition-delay: 1.1s;
}

.is-visible .visual-card p {
  opacity: 1;
  transform: translateY(0);
}

.visual-bottom {
  position: relative;
  z-index: 1;
  display: flex;
  justify-content: space-between;
  border-top: 1px solid rgba(255, 255, 255, 0.2);
  padding-top: 20px;
  margin-top: 35px;
  color: #ffb3b3;
  font-weight: 700;

  opacity: 0;
  transition: opacity 0.8s ease;
  transition-delay: 1.2s;
}

.is-visible .visual-bottom {
  opacity: 1;
}

/* Keyframes */
@keyframes circleFloat {
  from {
    transform: translate(0, 0);
  }

  to {
    transform: translate(25px, 20px);
  }
}

/* Responsive */
@media (max-width: 900px) {
  .container {
    grid-template-columns: 1fr;
    gap: 45px;
  }

  .about-section {
    padding: 75px 0;
  }

  .about-visual {
    min-height: 320px;
  }
}

@media (max-width: 480px) {
  .about-content p {
    font-size: 15px;
  }

  .about-visual {
    padding: 30px;
  }

  .visual-number {
    font-size: 55px;
  }
}

/* Accessibility */
@media (prefers-reduced-motion: reduce) {
  .section-label,
  .about-content h2,
  .about-paragraph,
  .about-button,
  .about-visual,
  .visual-number,
  .visual-card h3,
  .visual-card p,
  .visual-bottom {
    opacity: 1;
    transform: none;
    transition: none;
  }

  .about-visual::before {
    animation: none;
  }
}
</style>
