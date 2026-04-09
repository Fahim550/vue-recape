<script setup>
import Navbar from '@/components/shared/Navbar.vue'
import { ref } from 'vue'
import { RouterView } from 'vue-router'

const search = ref('')

const handleSearch = (value) => {
  search.value = value
}
</script>

<template>
  <div class="min-h-screen flex flex-col">
    <header class="bg-gray-100 shadow">
      <div class="wrapper">
        <Navbar @search="handleSearch" />
      </div>
    </header>

    <main class="flex-1">
      <RouterView :search="search" />
    </main>
  </div>
</template>

<style scoped>
.logo {
  display: block;
  margin: 0 auto 2rem;
}
</style>
