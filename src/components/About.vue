<script setup>
</script>

<template>
  <section class="about" id="about">
    <div class="container about-container">
      <div class="about-content">
        <h2 class="section-title">About Samcards</h2>
        <div class="divider"></div>
        <p class="about-text">
          At Samcards, we are dedicated to helping businesses and individuals navigate the complexities of the modern digital landscape. With a focus on innovation and efficiency, we provide comprehensive solutions designed to streamline your workflows and integrate smart automation.
        </p>
        <p class="about-text">
          Our expertise spans across IT consultancy, systems development, and professional coaching. Whether you're looking to upgrade your IT infrastructure, develop custom software, or seek guidance in your career, our team is committed to delivering excellence and ensuring you stay ahead of the competition.
        </p>
        <p class="about-text">
          We believe in the power of technology to transform businesses and empower individuals. Let us partner with you to achieve your goals and unlock your full potential.
        </p>
      </div>
      <div class="about-image">
        <img src="/src/pcseated.png" alt="Team working together" />
      </div>
    </div>
  </section>
</template>

<style scoped>
.about {
  padding: 6rem 0;
  background-color: white;
}

.about-container {
  display: flex;
  align-items: center;
  gap: 4rem;
}

.about-content {
  flex: 1;
}

.section-title {
  font-size: 2.5rem;
  color: var(--dark-text);
  margin-bottom: 1rem;
  font-weight: 800;
}

.divider {
  height: 4px;
  width: 60px;
  background-color: var(--primary-blue);
  margin-bottom: 2rem;
}

.about-text {
  font-size: 1.1rem;
  color: #555;
  margin-bottom: 1.5rem;
  line-height: 1.8;
}

.about-image {
  flex: 1;
}

.about-image img {
  width: 100%;
  height: auto;
  border-radius: 8px;
  box-shadow: 0 10px 30px rgba(0,0,0,0.1);
}

@media (max-width: 992px) {
  .about-container {
    flex-direction: column;
  }
  
  .about-content {
    text-align: center;
  }
  
  .divider {
    margin: 0 auto 2rem auto;
  }
}
</style>