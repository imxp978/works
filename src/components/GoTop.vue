<template>
  <div class="text-end">
    <div v-if="showGoTop" @click="goTop" id="gotop">
      <svg id="arrow" xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-chevron-double-up" viewBox="0 0 16 16">
        <path fill-rule="evenodd" d="M7.646 2.646a.5.5 0 0 1 .708 0l6 6a.5.5 0 0 1-.708.708L8 3.707 2.354 9.354a.5.5 0 1 1-.708-.708z"/>
        <path fill-rule="evenodd" d="M7.646 6.646a.5.5 0 0 1 .708 0l6 6a.5.5 0 0 1-.708.708L8 7.707l-5.646 5.647a.5.5 0 0 1-.708-.708z"/>
      </svg>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
const showGoTop = ref(false);

function handleScroll () {
  showGoTop.value = window.scrollY > 100;
};

function goTop ()  {
  window.scrollTo({ top: 0, behavior: 'smooth' });
};

onMounted(() => {
  window.addEventListener('scroll', handleScroll);
});
</script>

<style scoped>

#gotop {
    bottom: 8vh;
    right: 10px;
    width: 50px;
    height: 50px;
    position: fixed;
    background: rgba(0, 0, 0, 0.2) !important;
    cursor: pointer;
    color: gray !important;
    transition: 0.3s;
    display: flex;
    justify-content: center;
    align-items: center;
    border-radius: 5px;
  }

  #arrow {
    color: white;
    position: absolute;
    transition: 0.3s;
    animation: blink 0.5s infinite;
  }

  @keyframes blink {
    0%, 100% {
      transform: translateY(0);
    }
    50% {
      transform: translateY(5px);
    }
  }

  #gotop:hover {
    background: rgba(0, 0, 0, 0.5) !important;
    transition: 0.5s;
  }

</style>