<script setup lang="ts">
import { ref, onMounted } from "vue";

const message = ref("Loading...");
const health = ref("");

async function fetchData() {
  try {
    const res = await fetch("http://localhost:3000/");
    const data = await res.json();
    message.value = data.message;
  } catch (e) {
    message.value = "Could not reach server";
  }

  try {
    const res = await fetch("http://localhost:3000/health");
    const data = await res.json();
    health.value = data.status;
  } catch {
    health.value = "unreachable";
  }
}

onMounted(fetchData);
</script>

<template>
  <div class="container">
    <h1>3cxtools</h1>
    <p>Bun + Elysia + Vue monorepo demo</p>
    <div class="card">
      <p><strong>Server:</strong> {{ message }}</p>
      <p><strong>Health:</strong> {{ health }}</p>
      <button @click="fetchData">Refresh</button>
    </div>
  </div>
</template>

<style scoped>
.container {
  max-width: 600px;
  margin: 4rem auto;
  font-family: system-ui, sans-serif;
  text-align: center;
}
.card {
  margin-top: 2rem;
  padding: 1.5rem;
  border: 1px solid #ddd;
  border-radius: 8px;
}
button {
  margin-top: 1rem;
  padding: 0.5rem 1rem;
  cursor: pointer;
}
</style>
