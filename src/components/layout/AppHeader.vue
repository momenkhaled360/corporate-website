<script setup lang="ts">
import { onMounted, ref } from 'vue'

const navLinks = [
  { title: 'الرئيسية', href: '#home' },
  { title: 'من نحن', href: '#about' },
  { title: 'خدماتنا', href: '#services' },
  { title: 'مشاريعنا', href: '#projects' },
  { title: 'تواصل معنا', href: '#contact' },
]

const isLoaded = ref(false)

onMounted(() => {
  requestAnimationFrame(() => {
    isLoaded.value = true
  })
})
</script>

<template>
  <header class="site-header" :class="{ 'is-loaded': isLoaded }">
    <div class="container">
      <!-- Company Logo -->
      <a href="#home" class="logo" aria-label="شركة المروج العربية - الصفحة الرئيسية">
        <img
          :src="'public/images/logo.jpeg'"
          alt="شعار شركة المروج العربية للمقاولات"
          class="logo-image"
        />
      </a>

      <!-- Navigation -->
      <nav class="navigation">
        <a
          v-for="(link, index) in navLinks"
          :key="link.href"
          :href="link.href"
          :style="{ '--link-index': index }"
        >
          {{ link.title }}
        </a>
      </nav>

      <!-- Contact Button -->
      <a href="#contact" class="contact-button">اطلب خدمة</a>
    </div>
  </header>
</template>

<style scoped>
.site-header {
  background: #28669b;
  padding: 2px 0;
  border-bottom: 3px solid #c62828;
  position: sticky;
  top: 0;
  z-index: 100;
  box-shadow: 0 4px 18px rgba(23, 74, 126, 0.15);

  /* Reveal Animation */
  opacity: 0;
  clip-path: inset(0 0 100% 0);
  transition:
    opacity 0.9s ease,
    clip-path 0.9s cubic-bezier(0.22, 1, 0.36, 1);
}

.site-header.is-loaded {
  opacity: 1;
  clip-path: inset(0 0 0 0);
}

.container {
  width: 94%;
  max-width: 1440px;
  min-height: 85px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 25px;
}

/* Logo */
.logo {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 180px;
  height: 110px;
  background: transparent;
  border-radius: 0;
  overflow: visible;
  flex-shrink: 0;
  text-decoration: none;

  opacity: 0;
  filter: blur(5px);
  transform: translateY(12px);

  transition:
    opacity 0.7s ease,
    filter 0.7s ease,
    transform 0.7s ease;
  transition-delay: 0.3s;
}

.is-loaded .logo {
  opacity: 1;
  filter: blur(0);
  transform: translateY(0);
}

.logo-image {
  width: 100%;
  height: 100%;
  object-fit: contain;
  display: block;
}

.logo:hover {
  opacity: 0.9;
}

/* Navigation */
.navigation {
  display: flex;
  align-items: center;
  gap: 28px;
}

.navigation a {
  color: #ffffff;
  font-family: 'Alexandria', sans-serif;
  font-size: 14px;
  font-weight: 600;
  text-decoration: none;
  position: relative;
  padding: 8px 0;
  white-space: nowrap;

  opacity: 0;
  filter: blur(4px);
  transform: translateY(15px);

  transition:
    color 0.3s ease,
    opacity 0.6s ease,
    filter 0.6s ease,
    transform 0.6s ease;

  transition-delay: calc(0.45s + var(--link-index) * 0.1s);
}

.is-loaded .navigation a {
  opacity: 1;
  filter: blur(0);
  transform: translateY(0);
}

.navigation a::after {
  content: '';
  position: absolute;
  bottom: 0;
  right: 0;
  width: 0;
  height: 2px;
  background: #e53935;
  transition: width 0.3s ease;
}

.navigation a:hover {
  color: #ffcccc;
}

.navigation a:hover::after {
  width: 100%;
}

/* Contact Button */
.contact-button {
  background: #c62828;
  color: #ffffff;
  padding: 11px 22px;
  border-radius: 6px;
  font-family: 'IBM Plex Sans Arabic', sans-serif;
  font-size: 14px;
  font-weight: 700;
  text-decoration: none;
  white-space: nowrap;
  flex-shrink: 0;

  opacity: 0;
  filter: blur(4px);
  transform: scale(0.9);

  transition:
    background 0.3s ease,
    transform 0.3s ease,
    box-shadow 0.3s ease,
    opacity 0.6s ease,
    filter 0.6s ease;
  transition-delay: 1s;
}

.is-loaded .contact-button {
  opacity: 1;
  filter: blur(0);
  transform: scale(1);
}

.contact-button:hover {
  background: #a91f1f;
  transform: translateY(-2px);
  box-shadow: 0 5px 15px rgba(198, 40, 40, 0.25);
}

/* Tablet */
@media (max-width: 1100px) {
  .container {
    min-height: 75px;
    gap: 18px;
  }

  .logo {
    width: 155px;
    height: 95px;
  }

  .navigation {
    gap: 18px;
  }

  .navigation a {
    font-size: 13px;
  }

  .contact-button {
    padding: 10px 16px;
    font-size: 13px;
  }
}

/* Mobile */
@media (max-width: 850px) {
  .container {
    min-height: auto;
    flex-wrap: wrap;
    justify-content: space-between;
    gap: 10px;
  }

  .logo {
    width: 140px;
    height: 85px;
  }

  .navigation {
    order: 3;
    width: 100%;
    overflow-x: auto;
    gap: 25px;
    padding: 6px 0;
    scrollbar-width: none;
  }

  .navigation::-webkit-scrollbar {
    display: none;
  }

  .navigation a {
    font-size: 13px;
  }
}

/* Small Mobile */
@media (max-width: 480px) {
  .site-header {
    padding: 3px 0;
  }

  .container {
    width: 92%;
    gap: 12px;
  }

  .logo {
    width: 120px;
    height: 72px;
  }

  .contact-button {
    padding: 9px 12px;
    font-size: 12px;
  }

  .navigation {
    gap: 22px;
  }
}

/* Accessibility */
@media (prefers-reduced-motion: reduce) {
  .site-header,
  .logo,
  .navigation a,
  .contact-button {
    opacity: 1;
    filter: none;
    transform: none;
    clip-path: none;
    transition: none;
  }
}
</style>
