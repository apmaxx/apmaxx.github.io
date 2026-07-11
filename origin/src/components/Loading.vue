<template>
  <div v-if="isLoading" class="loading-screen">
    <div class="loading-content">
      <div class="spinner"></div>
      <img src="../assets/elements.jpg" width="500px" />
      
      <div class="loading-bar">
        <div class="loading-progress" :style="{ width: progress + '%' }"></div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const emit = defineEmits(['loading-complete'])

const isLoading = ref(true)
const progress = ref(0)

onMounted(() => {
  const interval = setInterval(() => {
    progress.value += Math.random() * 25
    if (progress.value >= 100) {
      progress.value = 100
      clearInterval(interval)
      setTimeout(() => {
        isLoading.value = false
        emit('loading-complete')
      }, 500)
    }
  }, 200)
})
</script>

<style scoped>
.loading-screen {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgb(255, 255, 255);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 9999;
    animation: fadeOut 1s;
  animation-delay: 1.5s;
}

@keyframes fadeOut {
    from { opacity: 1; }
    to { opacity: 0; }  

}
@keyframes animation{
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}

.loading-content {
  text-align: center;
  color: white;
}


.loading-content h2 {
  font-size: 2rem;
  margin-bottom: 10px;
  font-weight: bold;
}

.loading-content p {
  font-size: 1.2rem;
  margin-bottom: 30px;
  opacity: 0.9;
}



/* Responsive design */
@media (max-width: 480px) {
  .loading-content h2 {
    font-size: 1.5rem;
  }

  .loading-content p {
    font-size: 1rem;
  }

  .loading-bar {
    width: 250px;
  }

  .spinner {
    width: 50px;
    height: 50px;
  }
}
</style>