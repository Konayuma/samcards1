<script setup>
import mukuka1 from '../mukuka3.png'
</script>

<template>
  <section class="hero" id="home">
    <div class="container hero-container">
      <div class="hero-content">
        <p class="subtitle">WE</p>
        <h1 class="title">
          <span class="highlight">DIGITIZE</span><br>
          YOUR<br>
          BUSINESS
        </h1>
        <div class="divider"></div>
        <p class="description">
          Streamline your workflows, integrate smart automation, and stay ahead of the competition with modern tech solutions.
        </p>
        <div class="cta-buttons">
          <a href="#services" class="btn">Our Services</a>
          <a href="#contact" class="btn btn-outline">Contact Us</a>
        </div>
      </div>
      <div class="hero-image">
        <div class="blue-circle"></div>
        <div class="image-placeholder">
          <img :src="mukuka1" alt="Samcards CEO" />
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero {
  background-color: #f4f6f9;
  padding: 6rem 0 0 0;
  overflow: hidden;
  position: relative;
}

/* Background tech pattern simulation */
.hero::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-image: radial-gradient(#e0e5ec 1px, transparent 1px);
  background-size: 20px 20px;
  opacity: 0.5;
  z-index: 0;
}

.hero-container {
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
  position: relative;
  z-index: 1;
}

.hero-content {
  flex: 1;
  max-width: 500px;
  padding-bottom: 4rem;
}

.subtitle {
  color: var(--primary-blue);
  font-weight: 700;
  letter-spacing: 1px;
  margin-bottom: 1rem;
  font-size: 2rem;
}

.title {
  font-size: 4.5rem;
  font-weight: 800;
  color: #000;
  margin-bottom: 1.5rem;
  line-height: 1.1;
}

.highlight {
  color: var(--primary-blue);
}

.divider {
  height: 2px;
  width: 100%;
  background-color: #000;
  margin-bottom: 1.5rem;
}

.description {
  font-size: 1.2rem;
  color: #333;
  margin-bottom: 2.5rem;
  max-width: 400px;
}

.cta-buttons {
  display: flex;
  gap: 1rem;
}

.btn-outline {
  background-color: transparent;
  color: var(--primary-blue);
  border: 2px solid var(--primary-blue);
}

.btn-outline:hover {
  background-color: var(--primary-blue);
  color: white;
}

.hero-image {
  flex: 1;
  position: relative;
  display: flex;
  justify-content: center;
  align-items: flex-end;
}

.blue-circle {
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  bottom: -280px;
  width: 750px;
  height: 750px;
  background-color: var(--primary-blue);
  border-radius: 50%;
  z-index: -1;
}

.image-placeholder {
  display: flex;
  align-items: flex-end;
}

.image-placeholder img {
  max-width: 100%;
  max-height: 700px;
  width: auto;
  display: block;
  object-fit: contain;
  object-position: bottom;
}

@media (max-width: 992px) {
  .hero-container {
    flex-direction: column;
    text-align: center;
  }
  
  .hero-content {
    margin-bottom: 4rem;
    max-width: 100%;
  }
  
  .description {
    margin: 0 auto 2.5rem auto;
  }
  
  .cta-buttons {
    justify-content: center;
  }
  
  .blue-circle {
    width: 360px;
    height: 360px;
    right: 50%;
    bottom: 0;
    transform: translateX(50%);
  }
}

@media (max-width: 768px) {
  .title {
    font-size: 3rem;
  }
}
</style>