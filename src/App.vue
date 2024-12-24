<script setup>
import Posts from './components/Posts.vue';
</script>

<template>
  <main class="app-container">
    <header class="app-header">
      <h1 class="header-title">My Blog Application</h1>
    </header>
    <section class="posts-section">
      <Posts />
    </section>
  </main>
</template>

<style scoped>
/* Main application container */
.app-container {
  font-family: Arial, sans-serif;
  background-color: #f8f9fa;
  color: #333;
  padding: 2rem;
  line-height: 1.6;
  display: flex;
  flex-direction: column;
  align-items: center;
  min-height: 100vh;
}

/* Header styling */
.app-header {
  background-color: #007bff;
  color: white;
  padding: 1.5rem;
  border-radius: 8px;
  width: 100%;
  text-align: center;
  margin-bottom: 2rem;
}

.header-title {
  font-size: 2rem;
  margin: 0;
}

/* Section styling for Posts */
.posts-section {
  background-color: white;
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 2rem;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  width: 80%;
  max-width: 800px;
}
</style>
