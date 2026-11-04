<script setup lang="ts">
import { onMounted, onUnmounted, ref } from 'vue'

const footerLinks = [
  { title: 'الرئيسية', href: '#home' },
  { title: 'من نحن', href: '#about' },
  { title: 'خدماتنا', href: '#services' },
  { title: 'مشاريعنا', href: '#projects' },
  { title: 'تواصل معنا', href: '#contact' },
]

const footerRef = ref<HTMLElement | null>(null)
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
    { threshold: 0.15 },
  )

  if (footerRef.value) {
    observer.observe(footerRef.value)
  }
})

onUnmounted(() => {
  observer?.disconnect()
})
</script>

<template>
  <footer ref="footerRef" class="site-footer" :class="{ 'is-visible': isVisible }">
    <div class="container">
      <div class="footer-main">
        <!-- Company Info -->
        <div class="footer-about footer-item">
          <a href="#home" class="footer-logo" aria-label="شركة المروج العربية - الصفحة الرئيسية">
            <img
              :src="'public/images/logo.jpeg'"
              alt="شعار شركة المروج العربية للمقاولات"
              class="footer-logo-image"
            />
          </a>

          <p>
            نقدم حلول الخرسانة الجاهزة ومنتجات البلك لتلبية احتياجات المشروعات الإنشائية، مع
            الاهتمام بالجودة والالتزام.
          </p>
        </div>

        <!-- Quick Links -->
        <div class="footer-links footer-item">
          <h3>روابط سريعة</h3>

          <ul>
            <li
              v-for="(link, index) in footerLinks"
              :key="link.href"
              :style="{ '--link-index': index }"
            >
              <a :href="link.href">{{ link.title }}</a>
            </li>
          </ul>
        </div>

        <!-- Contact -->
        <div class="footer-contact footer-item">
          <h3>تواصل معنا</h3>

          <p>الهاتف: أضف رقم الشركة</p>
          <p>البريد: أضف البريد الإلكتروني</p>
          <p>العنوان: أضف عنوان الشركة</p>

          <a href="#contact" class="footer-button">اطلب خدمة</a>
        </div>
      </div>

      <!-- Copyright -->
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
  background: #28669b;
  color: #ffffff;
  padding: 35px 0 0;
  border-top: 4px solid #c62828;
  overflow: hidden;
}

.container {
  width: 94%;
  max-width: 1440px;
  margin: auto;
}

/* Main Layout */
.footer-main {
  display: grid;
  grid-template-columns: 1.4fr 0.8fr 1fr;
  gap: 60px;
  padding-bottom: 35px;
}

.footer-about,
.footer-links,
.footer-contact {
  text-align: right;
}

/* Entrance Animation */
.footer-item {
  opacity: 0;
  transform: translateY(25px);
  transition:
    opacity 0.7s ease,
    transform 0.7s ease;
}

.footer-about {
  transform: translateX(25px);
}

.footer-links {
  transition-delay: 0.15s;
}

.footer-contact {
  transform: translateX(-25px);
  transition-delay: 0.3s;
}

.is-visible .footer-item {
  opacity: 1;
  transform: translate(0, 0);
}

/* Logo */
.footer-logo {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 125px;
  height: 75px;
  background: transparent;
  margin-bottom: 12px;
  text-decoration: none;
  transition:
    transform 0.3s ease,
    opacity 0.3s ease;
}

.footer-logo-image {
  display: block;
  width: 100%;
  height: 100%;
  object-fit: contain;
  background: transparent;
}

.footer-logo:hover {
  transform: translateY(-3px);
  opacity: 0.9;
}

/* Company Description */
.footer-about p {
  color: #e5edf5;
  font-size: 14px;
  line-height: 2;
  max-width: 400px;
  margin: 0;
}

/* Headings */
.footer-main h3 {
  font-family: 'Alexandria', sans-serif;
  font-size: 17px;
  font-weight: 700;
  margin: 8px 0 22px;
  color: #ffffff;
  position: relative;
  display: inline-block;
}

.footer-main h3::after {
  content: '';
  position: absolute;
  right: 0;
  bottom: -9px;
  width: 35px;
  height: 2px;
  background: #e53935;
  border-radius: 2px;
}

/* Quick Links */
.footer-links ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.footer-links li {
  margin-bottom: 12px;
  opacity: 0;
  transform: translateY(10px);
  transition:
    opacity 0.5s ease,
    transform 0.5s ease;
  transition-delay: calc(0.35s + var(--link-index) * 0.08s);
}

.is-visible .footer-links li {
  opacity: 1;
  transform: translateY(0);
}

.footer-links a {
  display: inline-block;
  color: #e5edf5;
  text-decoration: none;
  font-size: 14px;
  transition:
    color 0.3s ease,
    transform 0.3s ease;
}

.footer-links a:hover {
  color: #ffffff;
  transform: translateX(-5px);
}

/* Contact */
.footer-contact p {
  color: #e5edf5;
  font-size: 14px;
  margin: 0 0 13px;
  line-height: 1.8;
}

/* Button */
.footer-button {
  display: inline-block;
  margin-top: 10px;
  padding: 10px 22px;
  background: #c62828;
  color: #ffffff;
  border-radius: 6px;
  text-decoration: none;
  font-size: 14px;
  font-weight: 700;
  transition:
    background 0.3s ease,
    transform 0.3s ease,
    box-shadow 0.3s ease;
}

.footer-button:hover {
  background: #a91f1f;
  transform: translateY(-3px);
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.15);
}

/* Footer Bottom */
.footer-bottom {
  border-top: 1px solid rgba(255, 255, 255, 0.2);
  padding: 18px 0;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 20px;
  opacity: 0;
  transform: translateY(12px);
  transition:
    opacity 0.7s ease,
    transform 0.7s ease;
  transition-delay: 0.5s;
}

.is-visible .footer-bottom {
  opacity: 1;
  transform: translateY(0);
}

.footer-bottom p {
  color: #e0eaf3;
  font-size: 12px;
  margin: 0;
  line-height: 1.8;
}

.footer-bottom a {
  color: #ffffff;
  text-decoration: none;
  font-size: 13px;
  font-weight: 600;
  transition:
    color 0.3s ease,
    transform 0.3s ease;
}

.footer-bottom a:hover {
  color: #ffcccc;
  transform: translateY(-2px);
}

/* Tablet */
@media (max-width: 900px) {
  .footer-main {
    grid-template-columns: repeat(2, 1fr);
    gap: 35px;
  }

  .footer-about {
    grid-column: 1 / -1;
  }
}

/* Mobile */
@media (max-width: 550px) {
  .site-footer {
    padding-top: 30px;
  }

  .footer-main {
    grid-template-columns: 1fr;
    gap: 30px;
    padding-bottom: 30px;
  }

  .footer-about {
    grid-column: auto;
  }

  .footer-logo {
    width: 110px;
    height: 65px;
  }

  .footer-bottom {
    flex-direction: column;
    align-items: flex-start;
    gap: 10px;
  }
}

/* Accessibility */
@media (prefers-reduced-motion: reduce) {
  .footer-item,
  .footer-links li,
  .footer-bottom,
  .footer-logo,
  .footer-button,
  .footer-links a {
    opacity: 1;
    transform: none;
    transition: none;
  }
}
</style>
