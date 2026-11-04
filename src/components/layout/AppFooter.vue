<script setup lang="ts">
const footerLinks = [
  { title: 'الرئيسية', href: '#home' },
  { title: 'من نحن', href: '#about' },
  { title: 'خدماتنا', href: '#services' },
  { title: 'مشاريعنا', href: '#projects' },
  { title: 'تواصل معنا', href: '#contact' },
]
</script>

<template>
  <footer class="site-footer">
    <div class="container">
      <div class="footer-main">
        <!-- Company Info -->
        <div class="footer-about">
          <a href="#home" class="footer-logo">
            <span>شركة المروج العربية للمقاولات</span>
            <small>وأعمال توريد الخرسانة الجاهزة والبلك</small>
          </a>

          <p>
            نقدم حلول الخرسانة الجاهزة ومنتجات البلك لتلبية احتياجات المشروعات الإنشائية، مع
            الاهتمام بالجودة والالتزام.
          </p>
        </div>

        <!-- Quick Links -->
        <div class="footer-links">
          <h3>روابط سريعة</h3>

          <ul>
            <li v-for="link in footerLinks" :key="link.href">
              <a :href="link.href">{{ link.title }}</a>
            </li>
          </ul>
        </div>

        <!-- Contact -->
        <div class="footer-contact">
          <h3>تواصل معنا</h3>

          <p>الهاتف: أضف رقم الشركة</p>
          <p>البريد: أضف البريد الإلكتروني</p>
          <p>العنوان: أضف عنوان الشركة</p>

          <a href="#contact" class="footer-button">اطلب خدمة</a>
        </div>
      </div>

      <div class="footer-bottom">
        <p>
          © {{ new Date().getFullYear() }}
          شركة المروج العربية للمقاولات. جميع الحقوق محفوظة.
        </p>

        <a href="#home">العودة للأعلى ↑</a>
      </div>
    </div>
  </footer>
</template>

<style scoped>
.site-footer {
  background: #0f304f;
  color: #ffffff;
  padding: 75px 0 0;
  border-top: 4px solid #c62828;
}

.container {
  width: 94%;
  max-width: 1440px;
  margin: auto;
}

.footer-main {
  display: grid;
  grid-template-columns: 1.4fr 0.8fr 1fr;
  gap: 70px;
  padding-bottom: 55px;
}

.footer-about,
.footer-links,
.footer-contact {
  text-align: right;
}

.footer-logo {
  display: inline-flex;
  flex-direction: column;
  gap: 7px;
  text-decoration: none;
  margin-bottom: 20px;
}

.footer-logo span {
  font-family: 'Alexandria', sans-serif;
  font-size: 23px;
  font-weight: 900;
  color: #ffffff;
}

.footer-logo small {
  font-family: 'IBM Plex Sans Arabic', sans-serif;
  font-size: 13px;
  color: #ffb3b3;
  font-weight: 600;
}

.footer-about p {
  color: #c5d1dc;
  font-size: 15px;
  line-height: 2.1;
  max-width: 400px;
}

.footer-main h3 {
  font-family: 'Alexandria', sans-serif;
  font-size: 18px;
  margin: 5px 0 25px;
  color: #e53935;
}

.footer-links ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.footer-links li {
  margin-bottom: 15px;
}

.footer-links a {
  color: #c5d1dc;
  text-decoration: none;
  font-size: 15px;
  transition: color 0.3s ease;
}

.footer-links a:hover {
  color: #ffb3b3;
}

.footer-contact p {
  color: #c5d1dc;
  font-size: 14px;
  margin-bottom: 17px;
}

.footer-button {
  display: inline-block;
  margin-top: 12px;
  padding: 11px 24px;
  background: #c62828;
  color: #ffffff;
  border-radius: 6px;
  text-decoration: none;
  font-weight: 800;
  transition: 0.3s ease;
}

.footer-button:hover {
  background: #a91f1f;
  transform: translateY(-3px);
}

.footer-bottom {
  border-top: 1px solid rgba(255, 255, 255, 0.13);
  padding: 22px 0;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 20px;
}

.footer-bottom p {
  color: #aebdca;
  font-size: 13px;
  margin: 0;
  line-height: 1.8;
}

.footer-bottom a {
  color: #ffb3b3;
  text-decoration: none;
  font-size: 14px;
  font-weight: 700;
  transition: color 0.3s ease;
}

.footer-bottom a:hover {
  color: #e53935;
}

/* Responsive */
@media (max-width: 900px) {
  .footer-main {
    grid-template-columns: repeat(2, 1fr);
    gap: 40px;
  }

  .footer-about {
    grid-column: 1 / -1;
  }
}

@media (max-width: 550px) {
  .site-footer {
    padding-top: 55px;
  }

  .footer-main {
    grid-template-columns: 1fr;
    gap: 35px;
  }

  .footer-about {
    grid-column: auto;
  }

  .footer-bottom {
    flex-direction: column;
    align-items: flex-start;
  }

  .footer-logo span {
    font-size: 20px;
  }
}
</style>
