<template>
  <section id="about" class="about-section">
    <div class="container">
      <div class="about-content">
        <span class="section-label">من نحن</span>

        <h2>
          خبرة في البناء...
          <span>وثقة في كل مشروع</span>
        </h2>

        <p>
          شركة المروج العربية للخرسانة الجاهزة والبلك، نعمل على تقديم حلول متكاملة في مجال الخرسانة
          الجاهزة ومنتجات البلك، مع الالتزام بأعلى معايير الجودة والدقة في التنفيذ.
        </p>

        <p>
          نسعى إلى أن نكون شريكاً موثوقاً لعملائنا من خلال توفير منتجات عالية الجودة، والالتزام
          بمواعيد التسليم، وتلبية احتياجات مختلف المشروعات.
        </p>

        <a href="#contact" class="about-button"> تواصل معنا </a>
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

.about-content {
  text-align: right;
}

.section-label {
  display: inline-block;
  color: #f28c28;
  font-size: 16px;
  font-weight: 800;
  margin-bottom: 18px;
}

.about-content h2 {
  font-family: 'Alexandria', sans-serif;
  font-size: clamp(28px, 3vw, 42px);
  line-height: 1.6;
  color: #23476a;
  margin: 0 0 25px;
  font-weight: 800;
}

.about-content h2 span {
  display: block;
  color: #f28c28;
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
  background: #23476a;
  color: #ffffff;
  border-radius: 6px;
  text-decoration: none;
  font-weight: 700;
  transition: 0.3s ease;
}

.about-button:hover {
  background: #f28c28;
  transform: translateY(-3px);
}

.about-visual {
  min-height: 390px;
  background: linear-gradient(145deg, #23476a, #142b45);
  border-radius: 12px;
  padding: 45px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  position: relative;
  overflow: hidden;
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
  color: #f28c28;
  display: block;
  margin-bottom: 15px;
}

.visual-card h3 {
  font-family: 'Alexandria', sans-serif;
  font-size: 25px;
  margin: 0 0 15px;
}

.visual-card p {
  color: #e2eaf2;
  font-size: 16px;
  line-height: 2;
  max-width: 400px;
}

.visual-bottom {
  position: relative;
  z-index: 1;
  display: flex;
  justify-content: space-between;
  border-top: 1px solid rgba(255, 255, 255, 0.2);
  padding-top: 20px;
  margin-top: 35px;
  color: #ffb15c;
  font-weight: 700;
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
</style>
