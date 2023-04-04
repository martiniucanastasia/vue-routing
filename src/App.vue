<script setup>
import { RouterView, RouterLink } from "vue-router"

</script>

<template>
  <main>
    <div class="links">
      <RouterLink active-class="active" to="/">Home</RouterLink>
      <RouterLink active-class="active" to="/about">About</RouterLink>
    </div>
    <RouterView />
  </main>
</template>


<style scoped>
.links {
  display: flex;
  justify-content: center;
  font-size: 20px;
  padding: 20px 0;
  gap: 20px;
}

.links a {
  text-decoration: none;
  color: #3E54AC;
}

.active {
  font-weight: bold;
}
</style>