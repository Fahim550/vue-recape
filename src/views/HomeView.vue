<script setup>
import BlogList from '@/components/BlogList.vue'
import BlogCatagory from '@/components/shared/BlogCatagory.vue'

import { blogs } from '@/data'
import { computed, ref } from 'vue'
const blogList = ref(blogs)
console.log('blogs', blogList)
const props = defineProps({
  search: String,
})

const selectCategory = ref('')

const handleCategory = (category) => {
  selectCategory.value = category
  console.log('category show', category)
}

console.log('selectcategory', selectCategory.value)

const filteredBlogs = computed(() => {
  const query = props.search?.toLowerCase() || ''
  const category = selectCategory?.value?.toLowerCase() || ''

  return blogList.value.filter((blog) => {
    const matchSearch = query ? blog.title.toLowerCase().includes(query) : true
    const matchCategory = category ? blog.category.toLocaleLowerCase().includes(category) : true
    return matchSearch && matchCategory
  })
})

console.log('filteredBlogs', filteredBlogs)
</script>

<template>
  <main>
    <h1 class="text-3xl text-green-500">This is a home page</h1>
    <div class="flex gap-4">
      <BlogList :blogList="filteredBlogs" />
      <BlogCatagory @selectCategory="handleCategory" />
    </div>
  </main>
</template>
