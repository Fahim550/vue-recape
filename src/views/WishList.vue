<template>
  <div class="max-w-screen-xl mx-auto p-16">
    <h1 class="text-3xl text-green-500 mb-8">This is a wishlist page</h1>
    <div class="sm:grid lg:grid-cols-3 sm:grid-cols-2 gap-10">
      <div
        class="hover:bg-gray-900 hover:text-white transition duration-300 max-w-sm rounded overflow-hidden shadow-lg"
        v-for="blog in wishList"
        :key="blog.id"
      >
        <div class="py-4 px-8">
          <img :src="blog?.authorImage" class="rounded-full h-12 w-12 mb-4" />
          <!-- < href="#"> -->
          <h4 class="text-lg mb-3 font-semibold">{{ blog.title }}</h4>
          <p class="mb-2 text-sm text-gray-600">
            {{ blog.description }}
          </p>
          <img :src="blog?.blogImage" class="w-100" />
          <hr class="mt-4" />
          <span class="text-xs">{{ blog.category }}</span>
          &nbsp;<span class="text-xs text-gray-500">{{ blog.tag }}</span>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
const wishList = JSON.parse(localStorage.getItem('wishList')) || []
</script>
