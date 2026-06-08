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
        <a href="#services">Services</a>
        <a href="#contact">Contact</a>
      </nav>
    </div>
  </header>
</template>

<style scoped>
.navbar {
  background-color: white;
  box-shadow: 0 2px 10px rgba(0,0,0,0.05);
  position: sticky;
  top: 0;
  z-index: 100;
}

.nav-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 92px;
}

.logo a {
  text-decoration: none;
  display: inline-block;
}

.logo-img {
  height: 72px;
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
  font-weight: 600;
  color: var(--dark-text);
  transition: color 0.3s;
}

.nav-links a:hover {
  color: var(--primary-blue);
}

@media (max-width: 768px) {
  .nav-links {
    display: none; /* Simple mobile menu hidden for now */
  }
}
</style>