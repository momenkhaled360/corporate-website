<script setup lang="ts">
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
</script>

<template>
  <section id="projects" class="projects-section">
    <div class="container">
      <div class="section-heading">
        <span class="section-label">مشاريعنا</span>
        <h2>أعمالنا تعكس <span>جودة ما نقدمه</span></h2>
        <p>نساهم في تلبية احتياجات المشروعات المختلفة من خلال منتجات وخدمات الخرسانة والبلك.</p>
      </div>

      <div class="projects-grid">
        <article v-for="(project, index) in projects" :key="project.title" class="project-card">
          <div class="project-image">
            <img :src="project.image" :alt="project.title" />

            <span class="project-number"> 0{{ index + 1 }} </span>

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
  color: #64748b;
  font-size: 17px;
  line-height: 2;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 25px;
}

.project-card {
  overflow: hidden;
  border-radius: 10px;
}

.project-image {
  position: relative;
  height: 370px;
  overflow: hidden;
  background: #23476a;
}

.project-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.5s ease;
}

.project-card:hover img {
  transform: scale(1.08);
}

.project-image::after {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(to top, rgba(20, 43, 69, 0.95), rgba(20, 43, 69, 0.05) 70%);
}

.project-number {
  position: absolute;
  top: 20px;
  right: 20px;
  z-index: 1;
  color: #ffffff;
  font-family: 'Alexandria', sans-serif;
  font-size: 20px;
  font-weight: 800;
}

.project-overlay {
  position: absolute;
  bottom: 0;
  right: 0;
  width: 100%;
  padding: 30px;
  z-index: 1;
  color: #ffffff;
  text-align: right;
}

.project-overlay span {
  color: #ffb15c;
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
</style>
