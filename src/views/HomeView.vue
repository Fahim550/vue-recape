<script setup>
import BlogList from '@/components/BlogList.vue'

import { blogs } from '@/data'
import { ref } from 'vue'
const blogList = ref(blogs)
console.log('blogs', blogList)
</script>

<template>
  <main>
    <!-- <TheWelcome /> -->
    <h1 class="text-3xl text-green-500">This is a home page</h1>
    <BlogList :blogList="blogList" />
  </main>
</template>
