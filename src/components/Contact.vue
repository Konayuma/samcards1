<script setup>
import { ref } from 'vue'
import { Call02Icon, AiMail01Icon, Linkedin01Icon, Facebook01Icon, MailSend01Icon } from 'hugeicons-vue'

const form = ref({ name: '', email: '', message: '' })

const infoItems = [
  { icon: Call02Icon,    label: 'Call or WhatsApp', value: '+260 961 850 020' },
  { icon: AiMail01Icon,  label: 'Email',            value: 'sam.mukuka@gmail.com' },
  { icon: Linkedin01Icon,label: 'LinkedIn',         value: '/samcards' },
  { icon: Facebook01Icon,label: 'Facebook',         value: '/samcards' },
]

const submitForm = () => {
  const subject = encodeURIComponent(`Inquiry from ${form.value.name}`)
  const body = encodeURIComponent(`Name: ${form.value.name}\nEmail: ${form.value.email}\n\nMessage:\n${form.value.message}`)
  window.location.href = `mailto:sam.mukuka@gmail.com?subject=${subject}&body=${body}`
}
</script>

<template>
  <section class="contact" id="contact">
    <div class="container">
      <div class="contact-wrapper">

        <!-- Left info panel -->
        <div class="contact-info">
          <p class="info-eyebrow">LET'S TALK</p>
          <h2 class="section-title">Get In Touch</h2>
          <div class="divider"></div>
          <p class="contact-desc">
            Ready to digitize your business or take the next step in your career? Reach out — we'd love to hear from you.
          </p>

          <div class="info-items">
            <div v-for="item in infoItems" :key="item.label" class="info-item">
              <div class="info-icon-wrap">
                <component :is="item.icon" size="22" />
              </div>
              <div class="details">
                <span class="detail-label">{{ item.label }}</span>
                <span class="detail-value">{{ item.value }}</span>
              </div>
            </div>
          </div>

          <!-- Decorative blobs -->
          <div class="blob blob-1"></div>
          <div class="blob blob-2"></div>
        </div>

        <!-- Right form panel -->
        <div class="contact-form-container">
          <h3 class="form-title">Send a Message</h3>
          <p class="form-subtitle">We'll get back to you within 24 hours.</p>

          <form @submit.prevent="submitForm" class="contact-form">
            <div class="form-row">
              <div class="form-group">
                <label for="name">Your Name</label>
                <input type="text" id="name" v-model="form.name" required placeholder="Your full name" />
              </div>
              <div class="form-group">
                <label for="email">Your Email</label>
                <input type="email" id="email" v-model="form.email" required placeholder="your@email.com" />
              </div>
            </div>

            <div class="form-group">
              <label for="message">Message</label>
              <textarea id="message" v-model="form.message" rows="6" required placeholder="Tell us how we can help you..."></textarea>
            </div>

            <button type="submit" class="btn submit-btn">
              <MailSend01Icon size="18" />
              Send Message
            </button>
          </form>
        </div>

      </div>
    </div>
  </section>
</template>

<style scoped>
.contact {
  padding: 6rem 0;
  background: linear-gradient(160deg, #f4f6f9 0%, #eef1f7 100%);
}

.contact-wrapper {
  display: flex;
  gap: 0;
  border-radius: 20px;
  box-shadow: 0 25px 60px rgba(0, 0, 0, 0.1);
  overflow: hidden;
}

/* ── Left panel ── */
.contact-info {
  flex: 1;
  padding: 4rem 3rem;
  background: linear-gradient(145deg, var(--primary-blue) 0%, #2a6ead 100%);
  color: white;
  position: relative;
  overflow: hidden;
}

.info-eyebrow {
  font-size: 0.82rem;
  font-weight: 700;
  letter-spacing: 3px;
  opacity: 0.75;
  margin-bottom: 0.75rem;
}

.section-title {
  font-size: 2.4rem;
  font-weight: 800;
  color: white;
  margin-bottom: 0.75rem;
  line-height: 1.15;
}

.divider {
  height: 3px;
  width: 50px;
  background: var(--gold, #d4af37);
  border-radius: 2px;
  margin-bottom: 1.5rem;
}

.contact-desc {
  font-size: 1rem;
  line-height: 1.7;
  opacity: 0.88;
  margin-bottom: 2.5rem;
}

/* Info items */
.info-items {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  position: relative;
  z-index: 1;
}

.info-item {
  display: flex;
  align-items: center;
  gap: 1.1rem;
  transition: transform 0.25s ease;
}

.info-item:hover {
  transform: translateX(5px);
}

.info-icon-wrap {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 46px;
  height: 46px;
  background: rgba(255, 255, 255, 0.15);
  border-radius: 12px;
  flex-shrink: 0;
  transition: background 0.3s ease;
}

.info-item:hover .info-icon-wrap {
  background: rgba(255, 255, 255, 0.28);
}

.details {
  display: flex;
  flex-direction: column;
  gap: 0.15rem;
}

.detail-label {
  font-size: 0.78rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 1px;
  opacity: 0.65;
}

.detail-value {
  font-size: 1rem;
  font-weight: 500;
}

/* Decorative blobs */
.blob {
  position: absolute;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.06);
  pointer-events: none;
}
.blob-1 { width: 280px; height: 280px; bottom: -80px; right: -80px; }
.blob-2 { width: 160px; height: 160px; top: -40px;   right: 40px; }

/* ── Right form panel ── */
.contact-form-container {
  flex: 1.3;
  padding: 4rem 3.5rem;
  background: white;
}

.form-title {
  font-size: 2rem;
  color: var(--dark-text);
  font-weight: 800;
  margin-bottom: 0.35rem;
}

.form-subtitle {
  font-size: 0.95rem;
  color: #888;
  margin-bottom: 2.25rem;
}

.form-row {
  display: flex;
  gap: 1.25rem;
}

.form-row .form-group {
  flex: 1;
}

.form-group {
  margin-bottom: 1.5rem;
}

label {
  display: block;
  font-size: 0.88rem;
  font-weight: 700;
  color: #444;
  margin-bottom: 0.45rem;
  letter-spacing: 0.3px;
}

input,
textarea {
  width: 100%;
  padding: 12px 16px;
  border: 1.5px solid #e5e7eb;
  border-radius: 10px;
  font-family: inherit;
  font-size: 0.97rem;
  color: var(--dark-text);
  background: #fafafa;
  transition: border-color 0.25s ease, box-shadow 0.25s ease, background 0.25s ease;
  box-sizing: border-box;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: var(--primary-blue);
  background: white;
  box-shadow: 0 0 0 4px rgba(91, 155, 213, 0.12);
}

textarea {
  resize: vertical;
  min-height: 140px;
}

.submit-btn {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.6rem;
  width: 100%;
  padding: 14px;
  font-size: 1rem;
  border-radius: 10px;
  margin-top: 0.5rem;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.submit-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 24px rgba(91, 155, 213, 0.35);
}

@media (max-width: 992px) {
  .contact-wrapper { flex-direction: column; }
  .contact-info,
  .contact-form-container { padding: 3rem 2rem; }
  .form-row { flex-direction: column; gap: 0; }
}
</style>