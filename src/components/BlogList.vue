<template>
  <div class="max-w-screen-xl mx-auto p-16">
    <div class="sm:grid lg:grid-cols-3 sm:grid-cols-2 gap-10">
      <div
        class="hover:bg-gray-900 hover:text-white transition duration-300 max-w-sm rounded overflow-hidden shadow-lg"
        v-for="blog in blogList"
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
          <button
            @click="addToWishlist(blog)"
            class="bg-pink-500 block py-1 px-2 rounded-2xl text-white cusrsor-pointer text-xs mt-2"
          >
            add wishlist
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  blogList: [],
})

const addToWishlist = (blog) => {
  let existingWishlist

  try {
    existingWishlist = JSON.parse(localStorage.getItem('wishList')) || []
  } catch (error) {
    existingWishlist = []
  }

  if (!Array.isArray(existingWishlist)) {
    existingWishlist = []
  }

  existingWishlist.push(blog)

  //   console.log('Existing Wishlist:', existingWishlist)
  localStorage.setItem('wishList', JSON.stringify(existingWishlist))
}
// console.log('wishList', localStorage.getItem('wishList'))
// console.log('addwishlist', addToWishlist)
// console.log('propsddar', props.blogList)
</script>
