<script setup lang="ts">
import { ref } from 'vue'

const name = ref('')
const phone = ref('')
const message = ref('')

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
</script>

<template>
  <section id="contact" class="contact-section">
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

          <div class="info-item">
            <span class="info-icon">☎</span>
            <div>
              <h4>رقم الهاتف</h4>
              <p>أضف رقم هاتف الشركة</p>
            </div>
          </div>

          <div class="info-item">
            <span class="info-icon">✉</span>
            <div>
              <h4>البريد الإلكتروني</h4>
              <p>أضف البريد الإلكتروني للشركة</p>
            </div>
          </div>

          <div class="info-item">
            <span class="info-icon">⌖</span>
            <div>
              <h4>العنوان</h4>
              <p>أضف عنوان الشركة</p>
            </div>
          </div>
        </div>

        <form class="contact-form" @submit.prevent="submitForm">
          <h3>أرسل لنا رسالة</h3>

          <div class="form-group">
            <label for="name">الاسم بالكامل</label>
            <input id="name" v-model="name" type="text" placeholder="اكتب اسمك" required />
          </div>

          <div class="form-group">
            <label for="phone">رقم الهاتف</label>
            <input id="phone" v-model="phone" type="tel" placeholder="اكتب رقم هاتفك" required />
          </div>

          <div class="form-group">
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
}

.container {
  width: 94%;
  max-width: 1440px;
  margin: auto;
}

.contact-heading {
  text-align: center;
  max-width: 700px;
  margin: 0 auto 55px;
}

.section-label {
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

.contact-content {
  display: grid;
  grid-template-columns: 0.8fr 1.2fr;
  gap: 30px;
  align-items: stretch;
}

.contact-info {
  background: linear-gradient(145deg, #174a7e, #0f304f);
  padding: 40px;
  border-radius: 10px;
  color: #ffffff;
  text-align: right;
  position: relative;
  overflow: hidden;
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

.info-item {
  display: flex;
  align-items: center;
  gap: 15px;
  margin-bottom: 28px;
  position: relative;
  z-index: 1;
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

.contact-form {
  background: #ffffff;
  padding: 40px;
  border-radius: 10px;
  text-align: right;
  box-shadow: 0 8px 30px rgba(23, 74, 126, 0.06);
}

.contact-form h3 {
  color: #174a7e;
  margin-bottom: 25px;
}

.form-group {
  margin-bottom: 20px;
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
  transition: all 0.3s ease;
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
  transition: 0.3s ease;
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
</style>
