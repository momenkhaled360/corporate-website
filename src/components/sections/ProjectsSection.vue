<script setup lang="ts">
import { onMounted, onUnmounted, ref } from 'vue'

const projects = [
  {
    title: 'المشروعات السكنية',
    category: 'خرسانة جاهزة',
    image: 'public/images/project-1.jpg',
  },
  {
    title: 'المشروعات التجارية',
    category: 'أعمال البناء والتشييد',
    image: 'public/images/project-2.jpg',
  },
  {
    title: 'مشروعات البنية التحتية',
    category: 'توريد الخرسانة',
    image: 'public/images/project-3.jpg',
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
    id="projects"
    ref="sectionRef"
    class="projects-section"
    :class="{ 'is-visible': isVisible }"
  >
    <div class="container">
      <div class="section-heading">
        <span class="section-label">مشاريعنا</span>
        <h2>أعمالنا تعكس <span>جودة ما نقدمه</span></h2>
        <p>نساهم في تلبية احتياجات المشروعات المختلفة من خلال منتجات وخدمات الخرسانة والبلك.</p>
      </div>

      <div class="projects-grid">
        <article
          v-for="(project, index) in projects"
          :key="project.title"
          class="project-card"
          :style="{ '--project-index': index }"
        >
          <div class="project-image">
            <img :src="project.image" :alt="project.title" />

            <span class="project-number">0{{ index + 1 }}</span>

            <div class="project-overlay">
              <span>{{ project.category }}</span>
              <h3>{{ project.title }}</h3>
            </div>
          </div>
        </article>
      </div>
    </div>
  </section>
</template>

<style scoped>
.projects-section {
  padding: 110px 0;
  background: #ffffff;
  overflow: hidden;
}

.container {
  width: 94%;
  max-width: 1440px;
  margin: auto;
}

/* Section Heading */
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
  color: #64748b;
  font-size: 17px;
  line-height: 2;
}

/* Projects Grid */
.projects-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 25px;
}

/* Project Card Animation */
.project-card {
  overflow: hidden;
  border-radius: 10px;

  opacity: 0;
  transform: translateY(50px) scale(0.97);

  transition:
    opacity 0.8s ease,
    transform 0.8s ease,
    box-shadow 0.4s ease;

  transition-delay: calc(var(--project-index) * 0.2s);
}

.is-visible .project-card {
  opacity: 1;
  transform: translateY(0) scale(1);
}

.project-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 18px 40px rgba(23, 74, 126, 0.16);
}

/* Project Image */
.project-image {
  position: relative;
  height: 370px;
  overflow: hidden;
  background: #174a7e;
}

.project-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transform: scale(1.08);
  transition: transform 0.8s ease;
}

.is-visible .project-image img {
  transform: scale(1);
}

.project-card:hover .project-image img {
  transform: scale(1.12);
}

/* Image Overlay */
.project-image::after {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(to top, rgba(15, 48, 79, 0.95), rgba(15, 48, 79, 0.05) 70%);
  opacity: 0.9;
  transition: opacity 0.4s ease;
}

.project-card:hover .project-image::after {
  opacity: 1;
}

/* Project Number */
.project-number {
  position: absolute;
  top: 20px;
  right: 20px;
  z-index: 1;
  color: #ffffff;
  font-family: 'Alexandria', sans-serif;
  font-size: 20px;
  font-weight: 800;
  background: #c62828;
  padding: 6px 12px;
  border-radius: 5px;

  opacity: 0;
  transform: translateY(-15px);
  transition:
    opacity 0.5s ease,
    transform 0.5s ease;
  transition-delay: calc(var(--project-index) * 0.2s + 0.3s);
}

.is-visible .project-number {
  opacity: 1;
  transform: translateY(0);
}

/* Project Details */
.project-overlay {
  position: absolute;
  bottom: 0;
  right: 0;
  width: 100%;
  padding: 30px;
  box-sizing: border-box;
  z-index: 1;
  color: #ffffff;
  text-align: right;

  transform: translateY(20px);
  opacity: 0.85;
  transition:
    transform 0.5s ease,
    opacity 0.5s ease;
}

.is-visible .project-overlay {
  transform: translateY(0);
  opacity: 1;
}

.project-card:hover .project-overlay {
  transform: translateY(-8px);
}

.project-overlay span {
  color: #ffb3b3;
  font-size: 14px;
  font-weight: 700;
}

.project-overlay h3 {
  font-family: 'Alexandria', sans-serif;
  font-size: 21px;
  margin: 10px 0 0;
}

/* Responsive */
@media (max-width: 900px) {
  .projects-grid {
    grid-template-columns: repeat(2, 1fr);
  }

  .projects-section {
    padding: 80px 0;
  }
}

@media (max-width: 600px) {
  .projects-grid {
    grid-template-columns: 1fr;
  }

  .project-image {
    height: 320px;
  }

  .section-heading p {
    font-size: 15px;
  }
}

/* Accessibility */
@media (prefers-reduced-motion: reduce) {
  .section-heading,
  .project-card,
  .project-image img,
  .project-number,
  .project-overlay {
    opacity: 1;
    transform: none;
    transition: none;
  }
}
</style>
