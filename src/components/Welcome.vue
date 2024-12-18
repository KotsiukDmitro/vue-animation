<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

const layer = ref<null | HTMLElement>(null)

const movePlane = () => {
  const scrollY = window.scrollY

  if (layer.value) {
    layer.value.style.left = `${scrollY}px`
  }
}

onMounted(() => {
  window.addEventListener('scroll', movePlane)
})

onUnmounted(() => {
  window.removeEventListener('scroll', movePlane)
})
</script>

<template>
  <div class="root text-white bg-[#020b1e]">
    <div ref="layer" class="fixed left-0 h-screen w-full bg-[#020b1e]">
      <div
        class="absolute left-1/2 top-1/2 -translate-x-1/2 -translate-y-1/2 text-5xl font-bold tracking-wider text-center"
      >
        Доброго вечора ми з
        <div class="text-9xl relative">
          <span
            class="accent-stroke absolute left-1/2 top-1/2 -translate-x-1/2 -translate-y-1/2 text-transparent"
            >України</span
          ><br />
          <span
            class="accent-wave absolute left-1/2 top-1/2 -translate-x-1/2 -translate-y-1/2 text-transparent"
            >України</span
          ><br />
        </div>
      </div>
      <img src="/images/plane.png" alt="plane" class="plane h-screen absolute z-10 left-[-50vh]" />
    </div>
    <div class="bg-1 bg-fixed bg-cover h-[240vh]"></div>
    <div class="content h-[50vh] flex justify-center items-center text-center">
      <div class="text-5xl font-extralight tracking-wide uppercase text-white">
        Welcome to
        <div class="textUkr">Ukraine</div>
      </div>
    </div>
    <div class="bg-2 bg-fixed bg-cover h-[130vh]"></div>
  </div>
</template>

<style scoped>
@keyframes wave {
  0%, 100% {
    clip-path: polygon(0% 39%, 9% 41%, 18% 45%, 24% 50%, 31% 55%, 39% 60%, 46% 62%, 53% 62%, 62% 59%, 68% 54%, 76% 50%, 83% 49%, 90% 50%, 97% 52%, 100% 54%, 100% 100%, 0% 100%)
  }
    
  50% {
    clip-path: polygon(0 49%, 5% 53%, 11% 57%, 16% 59%, 28% 64%, 38% 57%, 41% 58%, 48% 56%, 54% 58%, 64% 62%, 71% 66%, 79% 68%, 86% 66%, 92% 64%, 100% 62%, 100% 100%, 0% 100%)
  }

}
.root {
  font-family: 'Poppins' sans-serif;
}

.bg-1 {
  background-image: url('/images/forest.jpg');
}

.bg-2 {
  background-image: url('/images/mountains.png');
}

.textUkr {
  font-size: 128px;
  font-weight: 900;
  letter-spacing: 0;
  background: url('../images/mountains.png');
  background-size: cover;
  background-attachment: fixed;
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
}

.accent-stroke{
  -webkit-text-stroke: 2px #41BBE6;
}

.accent-wave {
  color: #41BBE6;
  animation: wave 4s ease-in-out infinite;
}
</style>
