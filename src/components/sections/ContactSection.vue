<script setup lang="ts">
import { onMounted, onUnmounted, ref } from 'vue'

const name = ref('')
const phone = ref('')
const message = ref('')

const sectionRef = ref<HTMLElement | null>(null)
const isVisible = ref(false)

let observer: IntersectionObserver | null = null

function submitForm() {
  if (!name.value || !phone.value || !message.value) {
    alert('من فضلك أكمل جميع البيانات')
    return
  }

  alert('تم استلام بياناتك بنجاح، سنتواصل معك قريباً')

  name.value = ''
  phone.value = ''
  message.value = ''
}

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
    id="contact"
    ref="sectionRef"
    class="contact-section"
    :class="{ 'is-visible': isVisible }"
  >
    <div class="container">
      <div class="contact-heading">
        <span class="section-label">تواصل معنا</span>

        <h2>دعنا نساعدك في <span>مشروعك القادم</span></h2>

        <p>يسعدنا استقبال استفساراتك ومساعدتك في اختيار الحلول المناسبة لاحتياجات مشروعك.</p>
      </div>

      <div class="contact-content">
        <div class="contact-info">
          <h3>بيانات التواصل</h3>
          <p>يمكنك التواصل معنا من خلال بيانات الاتصال التالية.</p>

          <div class="info-item" style="--item-index: 0">
            <span class="info-icon">☎</span>
            <div>
              <h4>رقم الهاتف</h4>
              <p>أضف رقم هاتف الشركة</p>
            </div>
          </div>

          <div class="info-item" style="--item-index: 1">
            <span class="info-icon">✉</span>
            <div>
              <h4>البريد الإلكتروني</h4>
              <p>أضف البريد الإلكتروني للشركة</p>
            </div>
          </div>

          <div class="info-item" style="--item-index: 2">
            <span class="info-icon">⌖</span>
            <div>
              <h4>العنوان</h4>
              <p>أضف عنوان الشركة</p>
            </div>
          </div>
        </div>

        <form class="contact-form" @submit.prevent="submitForm">
          <h3>أرسل لنا رسالة</h3>

          <div class="form-group" style="--field-index: 0">
            <label for="name">الاسم بالكامل</label>
            <input id="name" v-model="name" type="text" placeholder="اكتب اسمك" required />
          </div>

          <div class="form-group" style="--field-index: 1">
            <label for="phone">رقم الهاتف</label>
            <input id="phone" v-model="phone" type="tel" placeholder="اكتب رقم هاتفك" required />
          </div>

          <div class="form-group" style="--field-index: 2">
            <label for="message">رسالتك</label>
            <textarea
              id="message"
              v-model="message"
              rows="5"
              placeholder="اكتب تفاصيل استفسارك..."
              required
            ></textarea>
          </div>

          <button type="submit" class="submit-button">إرسال الرسالة</button>
        </form>
      </div>
    </div>
  </section>
</template>

<style scoped>
.contact-section {
  padding: 110px 0;
  background: #f5f7fa;
  overflow: hidden;
}

.container {
  width: 94%;
  max-width: 1440px;
  margin: auto;
}

/* Heading Animation */
.contact-heading {
  text-align: center;
  max-width: 700px;
  margin: 0 auto 55px;

  opacity: 0;
  transform: translateY(35px);
  transition:
    opacity 0.8s ease,
    transform 0.8s ease;
}

.is-visible .contact-heading {
  opacity: 1;
  transform: translateY(0);
}

.section-label {
  display: inline-block;
  color: #c62828;
  font-size: 16px;
  font-weight: 800;
}

.contact-heading h2 {
  font-family: 'Alexandria', sans-serif;
  color: #174a7e;
  font-size: clamp(28px, 3vw, 40px);
  line-height: 1.6;
  margin: 15px 0;
}

.contact-heading h2 span {
  color: #c62828;
}

.contact-heading p {
  color: #64748b;
  font-size: 16px;
  line-height: 2;
}

/* Content Layout */
.contact-content {
  display: grid;
  grid-template-columns: 0.8fr 1.2fr;
  gap: 30px;
  align-items: stretch;
}

/* Contact Info Animation */
.contact-info {
  background: linear-gradient(145deg, #174a7e, #0f304f);
  padding: 40px;
  border-radius: 10px;
  color: #ffffff;
  text-align: right;
  position: relative;
  overflow: hidden;

  opacity: 0;
  transform: translateX(45px);
  transition:
    opacity 0.8s ease,
    transform 0.8s ease;
  transition-delay: 0.2s;
}

.is-visible .contact-info {
  opacity: 1;
  transform: translateX(0);
}

.contact-info::before {
  content: '';
  position: absolute;
  width: 220px;
  height: 220px;
  border: 35px solid rgba(255, 255, 255, 0.05);
  border-radius: 50%;
  bottom: -100px;
  left: -90px;
  transition: transform 0.8s ease;
}

.is-visible .contact-info::before {
  transform: scale(1.15);
}

.contact-info h3,
.contact-form h3 {
  font-family: 'Alexandria', sans-serif;
  font-size: 23px;
  margin: 0 0 15px;
}

.contact-info > p {
  color: #dceaf7;
  font-size: 15px;
  line-height: 2;
  margin-bottom: 35px;
}

/* Contact Info Items */
.info-item {
  display: flex;
  align-items: center;
  gap: 15px;
  margin-bottom: 28px;
  position: relative;
  z-index: 1;

  opacity: 0;
  transform: translateY(20px);
  transition:
    opacity 0.6s ease,
    transform 0.6s ease;
  transition-delay: calc(0.4s + var(--item-index) * 0.15s);
}

.is-visible .info-item {
  opacity: 1;
  transform: translateY(0);
}

.info-icon {
  min-width: 48px;
  height: 48px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: #c62828;
  border-radius: 8px;
  font-size: 22px;

  transition:
    transform 0.3s ease,
    background 0.3s ease;
}

.info-item:hover .info-icon {
  background: #e53935;
  transform: scale(1.1) rotate(-5deg);
}

.info-item h4 {
  margin: 0 0 7px;
  font-size: 16px;
}

.info-item p {
  color: #dceaf7;
  margin: 0;
  font-size: 14px;
}

/* Form Animation */
.contact-form {
  background: #ffffff;
  padding: 40px;
  border-radius: 10px;
  text-align: right;
  box-shadow: 0 8px 30px rgba(23, 74, 126, 0.06);

  opacity: 0;
  transform: translateX(-45px);
  transition:
    opacity 0.8s ease,
    transform 0.8s ease,
    box-shadow 0.3s ease;
  transition-delay: 0.3s;
}

.is-visible .contact-form {
  opacity: 1;
  transform: translateX(0);
}

.contact-form:hover {
  box-shadow: 0 12px 35px rgba(23, 74, 126, 0.1);
}

.contact-form h3 {
  color: #174a7e;
  margin-bottom: 25px;
}

/* Form Fields */
.form-group {
  margin-bottom: 20px;

  opacity: 0;
  transform: translateY(20px);
  transition:
    opacity 0.6s ease,
    transform 0.6s ease;
  transition-delay: calc(0.5s + var(--field-index) * 0.15s);
}

.is-visible .form-group {
  opacity: 1;
  transform: translateY(0);
}

.form-group label {
  display: block;
  color: #174a7e;
  font-weight: 700;
  font-size: 14px;
  margin-bottom: 10px;
}

.form-group input,
.form-group textarea {
  width: 100%;
  box-sizing: border-box;
  padding: 14px 16px;
  border: 1px solid #dce4ec;
  border-radius: 6px;
  background: #f8fafc;
  color: #174a7e;
  font-family: 'IBM Plex Sans Arabic', sans-serif;
  font-size: 14px;
  outline: none;
  transition:
    border-color 0.3s ease,
    background 0.3s ease,
    box-shadow 0.3s ease;
}

.form-group input:focus,
.form-group textarea:focus {
  border-color: #c62828;
  background: #ffffff;
  box-shadow: 0 0 0 3px rgba(198, 40, 40, 0.08);
}

.form-group textarea {
  resize: vertical;
}

/* Submit Button */
.submit-button {
  width: 100%;
  border: none;
  padding: 15px;
  background: #c62828;
  color: #ffffff;
  border-radius: 6px;
  font-family: 'IBM Plex Sans Arabic', sans-serif;
  font-size: 16px;
  font-weight: 800;
  cursor: pointer;

  opacity: 0;
  transform: translateY(15px);
  transition:
    opacity 0.6s ease,
    transform 0.3s ease,
    background 0.3s ease,
    box-shadow 0.3s ease;
  transition-delay: 0.95s;
}

.is-visible .submit-button {
  opacity: 1;
  transform: translateY(0);
}

.submit-button:hover {
  background: #a91f1f;
  transform: translateY(-2px);
  box-shadow: 0 5px 15px rgba(198, 40, 40, 0.2);
}

/* Responsive */
@media (max-width: 900px) {
  .contact-content {
    grid-template-columns: 1fr;
  }

  .contact-section {
    padding: 80px 0;
  }
}

@media (max-width: 500px) {
  .contact-info,
  .contact-form {
    padding: 25px;
  }
}

/* Accessibility */
@media (prefers-reduced-motion: reduce) {
  .contact-heading,
  .contact-info,
  .contact-form,
  .info-item,
  .form-group,
  .submit-button {
    opacity: 1;
    transform: none;
    transition: none;
  }

  .contact-info::before {
    transform: none;
  }
}
</style>
