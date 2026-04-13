<template>
  <div>
    <h1 class="text-lg font-bold mb-4">Categories</h1>
    <ul>
      <li
        v-for="category in uniqueVategories"
        :key="category"
        class="text-md gap-3"
        @click="selectCategory(category)"
        :class="('cursor-pointer', [selectedCategory === category ? 'text-red-500 font-bold' : ''])"
      >
        {{ category }}
      </li>
    </ul>
  </div>
</template>
<script setup>
import { blogs } from '@/data'
import { computed, ref } from 'vue'
const blogList = ref(blogs)

const emit = defineEmits(['selectCategory'])

const uniqueVategories = computed(() => {
  const categories = blogList.value.map((blog) => blog.category)
  return [...new Set(categories)]
})

const selectedCategory = ref('')
const selectCategory = (category) => {
  // console.log('category', category)  
  selectedCategory.value = category
  emit('selectCategory', category)
}

// console.log('cat', selectedCategory.value)
</script>
