<template>
  <main class="container mx-auto mt-8">
    <div class="flex flex-wrap justify-between">
      <div class="w-full px-4 mb-8">
        <img :src="blog?.blogImage" alt="Featured Image" class="w-full h-64 object-cover rounded" />
        <h2 class="text-4xl font-bold mt-4 mb-2">{{ blog?.title }}</h2>
        <p class="text-gray-700 mb-4">
          {{ blog?.description }}
        </p>
      </div>
    </div>
  </main>
</template>

<script setup>
import { useRoute } from 'vue-router'

import { blogs } from '@/data'
import { computed, ref } from 'vue'

const route = useRoute()
const blogList = ref(blogs)

const blogId = Number(route.params.id)

const blog = computed(() => {
  return blogList.value.find((blog) => blog.id === blogId)
})
console.log('blog', blog?.value.title)
console.log('bloglist', blogList.value)
console.log('blogId', blogId)
</script>
