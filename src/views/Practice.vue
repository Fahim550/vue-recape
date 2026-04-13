<template>
  <div class="p-4">
    <h1>Practice</h1>
    <div>
      <h3>Watch:</h3>
      <p>
        Ask a yes/no question:
        <input v-model="question" :disabled="loading" class="border-2 border-gray-200" />
      </p>
      <p>Answer:{{ answer }}</p>
      <img :src="responseData.image" style="width: 200px" alt="" />
      <input
        type="text"
        placeholder="Type Phone Number"
        v-model="number"
        class="border-2 border-gray-200"
      />
    </div>
  </div>
</template>

<script setup>
import { ref, watch } from 'vue'
const number = ref('')

const question = ref('')
const answer = ref('Questions usually contain a question mark. ;-)')
const loading = ref(false)
const responseData = ref('')

// watch works directly on a ref
watch(question, async (newQuestion, oldQuestion) => {
  if (newQuestion.includes('?')) {
    loading.value = true
    answer.value = 'Thinking...'
    responseData.value = ''
    try {
      const res = await fetch('https://yesno.wtf/api')
      const resJson = await res.json()
      responseData.value = resJson
      answer.value = resJson.answer
    } catch (error) {
      answer.value = 'Error! Could not reach the API. ' + error
    } finally {
      loading.value = false
    }
  }
})

watch(number, (newValue, oldvalue) => {
  if (!Number(newValue)) {
    alert('Please Enter a Valid Number')
    number.value = oldvalue
  }

  if (newValue.length >= 11) {
    alert('An Otp Number is Send to Your Phone Number')
  }
  console.log('newValue', newValue)
  console.log('oldValue', oldvalue)
})
</script>
