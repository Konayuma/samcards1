<script setup>
import logo from '../samcardsflat.png'
</script>

<template>
  <header class="navbar">
    <div class="container nav-container">
      <div class="logo">
        <a href="#">
          <img :src="logo" alt="Samcards logo" class="logo-img" />
        </a>
      </div>
      <nav class="nav-links">
        <a href="#about">About</a>
        <a href="#services">Products & Services</a>
        <a href="#contact">Contact Us</a>
      </nav>
    </div>
  </header>
</template>

<style scoped>
.navbar {
  background-color: #ffffff;
  border-bottom: 1px solid rgba(255, 255, 255, 0.05);
  position: sticky;
  top: 0;
  z-index: 100;
}

.nav-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 64px;
}

.logo a {
  text-decoration: none;
  display: inline-block;
}

.logo-img {
  height: 48px;
  width: auto;
  display: block;
}

@media (max-width: 768px) {
  .logo-img {
    height: 48px;
  }
  .nav-container {
    height: 72px;
  }
}

.nav-links {
  display: flex;
  gap: 2rem;
}

.nav-links a {
  font-family: 'Inter', sans-serif;
  font-weight: 500;
  font-size: 0.95rem;
  color: #94a3b8;
  transition: color 0.3s;
}

.nav-links a:hover {
  color: #333333;
}

@media (max-width: 768px) {
  .nav-links {
    display: none; /* Simple mobile menu hidden for now */
  }
}
</style>