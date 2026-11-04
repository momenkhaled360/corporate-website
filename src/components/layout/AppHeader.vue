<script setup lang="ts">
const navLinks = [
  { title: 'الرئيسية', href: '#home' },
  { title: 'من نحن', href: '#about' },
  { title: 'خدماتنا', href: '#services' },
  { title: 'مشاريعنا', href: '#projects' },
  { title: 'تواصل معنا', href: '#contact' },
]
</script>

<template>
  <header class="site-header">
    <div class="container">
      <a href="#home" class="logo">
        <span class="logo-name">شركة المروج العربية للمقاولات</span>
        <span class="logo-description"> وأعمال توريد الخرسانة الجاهزة والبلك </span>
      </a>

      <nav class="navigation">
        <a v-for="link in navLinks" :key="link.href" :href="link.href">
          {{ link.title }}
        </a>
      </nav>

      <a href="#contact" class="contact-button">اطلب خدمة</a>
    </div>
  </header>
</template>

<style scoped>
.site-header {
  background: #23476a;
  padding: 15px 0;
  border-bottom: 3px solid #f28c28;
  position: sticky;
  top: 0;
  z-index: 100;
  box-shadow: 0 4px 18px rgba(35, 71, 106, 0.15);
}

.container {
  width: 94%;
  max-width: 1440px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 25px;
}

/* Logo */
.logo {
  display: flex;
  flex-direction: column;
  text-decoration: none;
  gap: 5px;
  flex-shrink: 0;
  min-width: 0;
}

.logo-name {
  font-family: 'Alexandria', sans-serif;
  font-size: 19px;
  font-weight: 800;
  color: #ffffff;
  line-height: 1.7;
  transition: color 0.3s ease;
}

.logo:hover .logo-name {
  color: #ffb15c;
}

.logo-description {
  font-family: 'IBM Plex Sans Arabic', sans-serif;
  font-size: 12px;
  font-weight: 500;
  color: #ffb15c;
  line-height: 1.7;
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
  transition: color 0.3s ease;
  position: relative;
  padding: 8px 0;
  white-space: nowrap;
}

.navigation a::after {
  content: '';
  position: absolute;
  bottom: 0;
  right: 0;
  width: 0;
  height: 2px;
  background: #f28c28;
  transition: width 0.3s ease;
}

.navigation a:hover {
  color: #ffb15c;
}

.navigation a:hover::after {
  width: 100%;
}

/* Contact Button */
.contact-button {
  background: #f28c28;
  color: #ffffff;
  padding: 11px 22px;
  border-radius: 6px;
  font-family: 'IBM Plex Sans Arabic', sans-serif;
  font-size: 14px;
  font-weight: 700;
  text-decoration: none;
  transition: all 0.3s ease;
  white-space: nowrap;
  flex-shrink: 0;
}

.contact-button:hover {
  background: #dc7615;
  transform: translateY(-2px);
  box-shadow: 0 5px 15px rgba(242, 140, 40, 0.25);
}

/* Tablet */
@media (max-width: 1100px) {
  .container {
    gap: 18px;
  }

  .logo-name {
    font-size: 17px;
  }

  .logo-description {
    font-size: 11px;
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
    flex-wrap: wrap;
    justify-content: space-between;
    gap: 15px;
  }

  .logo-name {
    font-size: 17px;
  }

  .navigation {
    order: 3;
    width: 100%;
    overflow-x: auto;
    gap: 25px;
    padding: 8px 0;
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
    padding: 12px 0;
  }

  .container {
    width: 92%;
    gap: 12px;
  }

  .logo-name {
    font-size: 15px;
  }

  .logo-description {
    font-size: 10px;
  }

  .contact-button {
    padding: 9px 12px;
    font-size: 12px;
  }

  .navigation {
    gap: 22px;
  }
}
</style>
