<script setup>
import logo from '../samcardsflat.png'
</script>

<template>
  <footer class="footer">
    <div class="container footer-container">
      <div class="footer-content">
        <div class="footer-logo">
          <a href="#">
            <img :src="logo" alt="Samcards logo" class="footer-logo-img" />
          </a>
        </div>
        <p class="footer-text">
          Digitize your business with modern tech solutions.
        </p>
        <div class="social-links">
          <a href="#" aria-label="LinkedIn">in</a>
          <a href="#" aria-label="Facebook">f</a>
        </div>
      </div>
      <div class="footer-bottom">
        <p>&copy; {{ new Date().getFullYear() }} Samcards. All rights reserved.</p>
      </div>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  background-color: #1a1a1a;
  color: white;
  padding: 4rem 0 2rem 0;
}

.footer-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

.footer-content {
  margin-bottom: 3rem;
}

.footer-logo a {
  display: inline-block;
  margin-bottom: 1rem;
  text-decoration: none;
}

.footer-logo-img {
  height: 96px;
  width: auto;
  display: block;
}

@media (max-width: 768px) {
  .footer-logo-img {
    height: 72px;
  }
}

.footer-text {
  color: #aaa;
  font-size: 1.1rem;
  margin-bottom: 2rem;
}

.social-links {
  display: flex;
  gap: 1rem;
  justify-content: center;
}

.social-links a {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 40px;
  height: 40px;
  background-color: rgba(255,255,255,0.1);
  border-radius: 50%;
  color: white;
  font-weight: bold;
  transition: background-color 0.3s, transform 0.3s;
}

.social-links a:hover {
  background-color: var(--primary-blue);
  transform: translateY(-3px);
}

.footer-bottom {
  border-top: 1px solid rgba(255,255,255,0.1);
  padding-top: 2rem;
  width: 100%;
  color: #888;
  font-size: 0.9rem;
}
</style>