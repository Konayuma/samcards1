<script setup>
import AiCoreHub from './AiCoreHub.vue'
</script>

<template>
  <section class="hero" id="home">
    <div class="hero-bg-glow"></div>
    <div class="container hero-container">
      <div class="hero-content">
        <h1 class="title">
          Revolutionize <br/>
          <span class="highlight">your business</span>
        </h1>
        <p class="description">
         Streamline your workflows, integrate smart automation and stay ahead of the competition with smart businesss solutions.</p>
        <div class="cta-buttons">
          <a href="#services" class="btn btn-primary">Products & Services</a>
          <a href="#contact" class="btn btn-outline">
            <span class="pulse-dot"></span> Contact Us
          </a>
        </div>
      </div>
      
      <div class="hero-graphic">
        <AiCoreHub />
      </div>
    </div>
  </section>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap');

.hero {
  background-color: #ffffff;
  padding: 5rem 0 2rem 0;
  overflow: hidden;
  position: relative;
  font-family: 'Inter', sans-serif;
  color: #fff;
}

/* Base glowing background for the hero */
.hero-bg-glow {
  position: absolute;
  top: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 100%;
  max-width: 1000px;
  height: 600px;
  background: radial-gradient(circle at top, rgba(0, 210, 255, 0.08) 0%, transparent 65%);
  z-index: 0;
  pointer-events: none;
}

.hero-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  position: relative;
  z-index: 1;
  text-align: center;
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

.hero-content {
  max-width: 800px;
  margin-bottom: 2rem;
  z-index: 2;
}

.title {
  font-size: 4.5rem;
  font-weight: 700;
  color: #a7a3a3;
  margin-bottom: 1.5rem;
  line-height: 1.15;
  letter-spacing: -0.02em;
}

.highlight {
  color: transparent;
  background-clip: text;
  -webkit-background-clip: text;
  background-image: linear-gradient(90deg, #a7a3a3 11%, #3B82F6 100%);
}

.description {
  font-size: 1.25rem;
  color: #94a3b8;
  margin: 0 auto 2.5rem auto;
  max-width: 650px;
  line-height: 1.6;
}

.cta-buttons {
  display: flex;
  gap: 1.2rem;
  justify-content: center;
  align-items: center;
}

.btn {
  padding: 0.8rem 1.8rem;
  border-radius: 8px;
  font-weight: 600;
  transition: all 0.3s ease;
  text-decoration: none;
  font-size: 1rem;
  display: inline-flex;
  align-items: center;
  justify-content: center;
}

.btn-primary {
  background: linear-gradient(135deg, #3B82F6, #2563eb);
  color: #ffffff;
  border: none;
  box-shadow: 0 2px 8px rgba(59, 130, 246, 0.25);
}

.btn-primary:hover {
  box-shadow: 0 4px 14px rgba(59, 130, 246, 0.35);
  transform: translateY(-2px);
}

.btn-outline {
  background: #f1f3f6;
  border: 1px solid #e2e8ef;
  color: #475569;
  gap: 0.6rem;
}

.btn-outline:hover {
  background: #e8ecf1;
  border-color: #cbd5e1;
}

.pulse-dot {
  width: 8px;
  height: 8px;
  background: #00D2FF;
  border-radius: 50%;
  border: 2px solid #050816;
  box-shadow: 0 0 0 0 rgba(0, 210, 255, 0.8);
  animation: pulseLight 2s infinite cubic-bezier(0.66, 0, 0, 1);
}

@keyframes pulseLight {
  to {
    box-shadow: 0 0 0 12px rgba(0, 210, 255, 0);
  }
}

.hero-graphic {
  width: 100%;
  display: flex;
  justify-content: center;
  margin-top: 2rem;
}

@media (max-width: 900px) {
  .title { font-size: 3.5rem; }
}

@media (max-width: 768px) {
  .title {
    font-size: 2.8rem;
  }
  .description {
    font-size: 1.1rem;
    padding: 0 1rem;
  }
  .cta-buttons {
    flex-direction: column;
    width: 100%;
    padding: 0 2rem;
  }
  .btn {
    width: 100%;
  }
}
</style>