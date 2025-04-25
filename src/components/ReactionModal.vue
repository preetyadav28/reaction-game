<template>
  <div class="overlay" @click="closeModal">
    <div class="modal">
      <h2>Click Me</h2>
    </div>
  </div>
</template>

<script setup>
  const emit = defineEmits()
  function closeModal() {
    emit('close')
  }
</script>

<style scoped>
  .overlay {
    position: fixed;
    top: 0;
    left: 0;
    width:100vw;
    height: 100vh;
    background-color: rgba(0,0,0,0.5);
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .modal {
    width:40%;
    height:40%;
    background-color: rgb(200,200,0);
    border-radius:5%;
    display:flex;
    align-items:center;
    justify-content:center;
  }
</style>