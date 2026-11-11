<script setup lang="ts">
// استبدل الرقم برقم الشركة بكود الدولة بدون +
const phoneNumber = '966567130574'
const whatsappMessage = 'السلام عليكم، أريد الاستفسار عن خدمات شركة المروج العربية.'

const whatsappLink = `https://wa.me/${phoneNumber}?text=${encodeURIComponent(whatsappMessage)}`
const callLink = `tel:+${phoneNumber}`
</script>

<template>
  <div class="floating-contact">
    <!-- WhatsApp -->
    <a
      :href="whatsappLink"
      class="contact-button whatsapp"
      target="_blank"
      rel="noopener noreferrer"
      aria-label="تواصل معنا عبر واتساب"
      title="تواصل عبر واتساب"
    >
      <svg viewBox="0 0 24 24" aria-hidden="true">
        <path
          fill="currentColor"
          d="M20.52 3.48A11.8 11.8 0 0 0 12.12 0C5.58 0 .25 5.33.25 11.87c0 2.09.55 4.13 1.6 5.93L.15 24l6.35-1.66a11.9 11.9 0 0 0 5.62 1.43h.01c6.54 0 11.87-5.33 11.87-11.87 0-3.17-1.24-6.15-3.48-8.42ZM12.13 21.7a9.8 9.8 0 0 1-5-.1l-.36-.14-3.77.99 1.01-3.68-.17-.38a9.8 9.8 0 1 1 8.29 3.31Zm5.37-7.34c-.3-.15-1.77-.87-2.04-.97-.27-.1-.47-.15-.67.15-.2.3-.77.97-.94 1.17-.17.2-.35.22-.65.07-.3-.15-1.26-.46-2.4-1.47-.89-.8-1.49-1.78-1.66-2.08-.17-.3-.02-.46.13-.61.13-.13.3-.35.45-.52.15-.17.2-.3.3-.5.1-.2.05-.37-.03-.52-.07-.15-.67-1.62-.92-2.22-.24-.58-.48-.5-.67-.51h-.57c-.2 0-.52.07-.79.37-.27.3-1.04 1.02-1.04 2.49s1.07 2.89 1.22 3.09c.15.2 2.1 3.2 5.08 4.49.71.31 1.27.5 1.7.64.71.23 1.36.2 1.87.12.57-.08 1.77-.72 2.02-1.42.25-.7.25-1.3.17-1.42-.07-.13-.27-.2-.57-.35Z"
        />
      </svg>
    </a>

    <!-- Phone -->
    <a :href="callLink" class="contact-button phone" aria-label="اتصل بنا" title="اتصل بنا">
      <svg viewBox="0 0 24 24" aria-hidden="true">
        <path
          fill="currentColor"
          d="M6.62 10.79a15.05 15.05 0 0 0 6.59 6.59l2.2-2.2a1 1 0 0 1 1.02-.24c1.12.37 2.33.56 3.57.56.55 0 1 .45 1 1V20c0 .55-.45 1-1 1C10.61 21 3 13.39 3 4c0-.55.45-1 1-1h3.5c.55 0 1 .45 1 1 0 1.24.19 2.45.56 3.57a1 1 0 0 1-.25 1.02l-2.19 2.2Z"
        />
      </svg>
    </a>
  </div>
</template>

<style scoped>
.floating-contact {
  position: fixed;
  right: 24px;
  bottom: 25px;
  z-index: 9999;
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.contact-button {
  width: 55px;
  height: 55px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  text-decoration: none;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
  transition:
    transform 0.3s ease,
    box-shadow 0.3s ease;
}

.contact-button svg {
  width: 27px;
  height: 27px;
}

.contact-button:hover {
  transform: translateY(-4px) scale(1.06);
  box-shadow: 0 7px 20px rgba(0, 0, 0, 0.25);
}

.whatsapp {
  background: #25d366;
}

.phone {
  background: #28669b;
}

@media (max-width: 550px) {
  .floating-contact {
    right: 15px;
    bottom: 18px;
    gap: 10px;
  }

  .contact-button {
    width: 49px;
    height: 49px;
  }

  .contact-button svg {
    width: 24px;
    height: 24px;
  }
}

@media (prefers-reduced-motion: reduce) {
  .contact-button {
    transition: none;
  }
}
</style>
