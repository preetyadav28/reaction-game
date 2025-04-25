<template>
  <div>
    <h2>Welcome to the Reaction Game</h2>
    <button @click='openModal'>Play</button>
    <ReactionModal v-if="showModal" @close="closeModal" />
    <template v-if='difference'>
      <h3>{{ difference }} ms</h3>
      <h2>{{ result }}</h2>
    </template>
  </div>
</template>

<script setup>
  import { ref, computed } from 'vue';
  import ReactionModal from './ReactionModal.vue'
  
  const showModal = ref(false);
  let openedAt = ref(0);
  let closedAt = ref(0);
  const difference = computed(() => {
    if(closedAt.value && openedAt.value){
      return closedAt.value - openedAt.value
    }
    return 0
  })
  const result = computed(() => {
    if(difference.value < 200) return 'Lightning ⚡'
    if(difference.value < 299) return 'Cheetah 🐆'
    if(difference.value < 399) return 'Average 🐾'
    if(difference.value < 499) return 'Tortoise 🐢'
    if(difference.value < 699) return 'Snail 🐌'
    if(difference.value > 700) return 'Too Slow 😕'
  })
  console.log('result', result)
  function openModal() {
      const randomNumber = Math.floor(Math.random() * 3) + 1
      setTimeout(() => {
        openedAt.value = Date.now()
        closedAt.value = 0
        showModal.value = true
      }, randomNumber * 1000)
  }
  function closeModal() {
     closedAt.value = Date.now()
     showModal.value = false
  }
</script>