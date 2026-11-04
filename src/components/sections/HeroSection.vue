<template>
  <section id="home" class="hero-section">
    <div class="hero-overlay"></div>

    <div class="container">
      <div class="hero-content">
        <span class="hero-label"> المروج العربية للخرسانة الجاهزة والبلك </span>

        <h1>
          نبني أساس المستقبل
          <span>بجودة تثق بها</span>
        </h1>

        <p>
          نقدم حلول الخرسانة الجاهزة والبلك بأعلى معايير الجودة، من خلال خبرة متميزة وإمكانيات تواكب
          احتياجات المشروعات الحديثة.
        </p>

        <div class="hero-actions">
          <a href="#contact" class="primary-button">اطلب خدمة</a>
          <a href="#about" class="secondary-button">اكتشف الشركة</a>
        </div>
      </div>
    </div>

    <div class="hero-bottom-line"></div>
  </section>
</template>

<style scoped>
.hero-section {
  position: relative;
  display: flex;
  align-items: center;
  min-height: calc(100svh - 101px);
  margin: 0;
  background-image: url('public/images/concrete-plant.jpg');
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
  overflow: hidden;

  /* Background animation */
  animation: heroBackgroundZoom 15s ease-in-out infinite alternate;
}

/* Blue Overlay */
.hero-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(90deg, rgba(15, 48, 79, 0.82), rgba(23, 74, 126, 0.68));
}

/* Container */
.container {
  width: 94%;
  max-width: 1440px;
  margin: 0 auto;
  position: relative;
  z-index: 1;
}

.hero-content {
  max-width: 750px;
  text-align: right;
  color: #ffffff;
  padding: 80px 0;
}

/* Label Animation */
.hero-label {
  display: inline-block;
  color: #ffb3b3;
  font-size: 16px;
  font-weight: 700;
  margin-bottom: 22px;

  opacity: 0;
  animation: slideFromRight 0.8s ease forwards;
  animation-delay: 0.2s;
}

/* Heading Animation */
.hero-content h1 {
  font-family: 'Alexandria', sans-serif;
  font-size: clamp(36px, 5vw, 62px);
  font-weight: 800;
  line-height: 1.5;
  margin: 0 0 20px;

  opacity: 0;
  animation: slideUp 0.9s ease forwards;
  animation-delay: 0.5s;
}

.hero-content h1 span {
  display: block;
  color: #e53935;
}

/* Paragraph Animation */
.hero-content p {
  font-family: 'IBM Plex Sans Arabic', sans-serif;
  max-width: 650px;
  font-size: 19px;
  font-weight: 400;
  line-height: 2;
  color: #f1f5f9;
  margin: 0 0 35px;

  opacity: 0;
  animation: slideUp 0.9s ease forwards;
  animation-delay: 0.8s;
}

/* Buttons */
.hero-actions {
  display: flex;
  align-items: center;
  gap: 16px;
  flex-wrap: wrap;
}

.hero-actions a {
  text-decoration: none;
  padding: 14px 32px;
  border-radius: 6px;
  font-size: 16px;
  font-weight: 700;
  transition: all 0.3s ease;

  opacity: 0;
  animation: slideUp 0.8s ease forwards;
}

.primary-button {
  background: #c62828;
  color: #ffffff;
  border: 1px solid #c62828;
  animation-delay: 1.1s !important;
}

.primary-button:hover {
  background: #a91f1f;
  border-color: #a91f1f;
  transform: translateY(-3px);
}

.secondary-button {
  border: 1px solid rgba(255, 255, 255, 0.8);
  color: #ffffff;
  animation-delay: 1.3s !important;
}

.secondary-button:hover {
  background: #ffffff;
  color: #174a7e;
  transform: translateY(-3px);
}

/* Bottom Accent Animation */
.hero-bottom-line {
  position: absolute;
  bottom: 0;
  right: 0;
  width: 35%;
  height: 5px;
  background: #c62828;

  transform: scaleX(0);
  transform-origin: right;
  animation: expandLine 1s ease forwards;
  animation-delay: 1.2s;
}

/* Keyframes */
@keyframes slideFromRight {
  from {
    opacity: 0;
    transform: translateX(45px);
  }

  to {
    opacity: 1;
    transform: translateX(0);
  }
}

@keyframes slideUp {
  from {
    opacity: 0;
    transform: translateY(35px);
  }

  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes heroBackgroundZoom {
  from {
    background-size: 100% 100%;
  }

  to {
    background-size: 110% 110%;
  }
}

@keyframes expandLine {
  to {
    transform: scaleX(1);
  }
}

/* Tablet */
@media (max-width: 768px) {
  .hero-section {
    min-height: calc(100svh - 101px);
    animation-duration: 20s;
  }

  .hero-overlay {
    background: rgba(15, 48, 79, 0.78);
  }

  .hero-content {
    padding: 65px 0;
  }

  .hero-content h1 {
    font-size: clamp(34px, 7vw, 46px);
  }

  .hero-content p {
    font-size: 16px;
  }

  .hero-actions a {
    padding: 12px 22px;
  }
}

/* Mobile */
@media (max-width: 480px) {
  .hero-section {
    min-height: calc(100svh - 101px);
  }

  .hero-content {
    padding: 55px 0;
  }

  .hero-label {
    font-size: 14px;
  }

  .hero-content h1 {
    font-size: 34px;
    line-height: 1.6;
  }

  .hero-content p {
    font-size: 15px;
    line-height: 1.9;
  }

  .hero-actions {
    align-items: stretch;
    flex-direction: column;
  }

  .hero-actions a {
    text-align: center;
  }
}

/* Accessibility: Reduce motion */
@media (prefers-reduced-motion: reduce) {
  .hero-section,
  .hero-label,
  .hero-content h1,
  .hero-content p,
  .hero-actions a,
  .hero-bottom-line {
    animation: none;
    opacity: 1;
    transform: none;
  }
}
</style>
