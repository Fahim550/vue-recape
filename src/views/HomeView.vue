<script setup>
import BlogList from '@/components/BlogList.vue'

import { blogs } from '@/data'
import { computed, ref } from 'vue'
const blogList = ref(blogs)
console.log('blogs', blogList)
const props = defineProps({
  search: String,
})

const filteredBlogs = computed(() => {
  const query = props.search?.toLowerCase() || ''
  if (!query) return blogList.value

  return blogList.value.filter((blog) => blog.title.toLowerCase().includes(query))
})

console.log('filteredBlogs', filteredBlogs)
</script>

<template>
  <main>
    <h1 class="text-3xl text-green-500">This is a home page</h1>
    <BlogList :blogList="filteredBlogs" />
  </main>
</template>
