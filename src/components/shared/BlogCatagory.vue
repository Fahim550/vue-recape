<template>
  <div>
    <h1>Blog Categories</h1>
    <ul>
      <li v-for="category in uniqueVategories" :key="category">{{ category }}</li>
    </ul>
  </div>
</template>
<script setup>
import { blogs } from '@/data'
import { computed, ref } from 'vue'
const blogList = ref(blogs)

const uniqueVategories = computed(() => {
  const categories = blogList.value.map((blog) => blog.category)
  return [...new Set(categories)]
})
</script>
