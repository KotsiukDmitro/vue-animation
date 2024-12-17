<script setup>
</script>

<template>
  <div class="main relative min-h-screen min-w-full bg-cover">
    <div class="section">
      <div class="rain absolute top-0 left-0 w-full h-full"></div>
    </div>
  </div>
</template>



<style scoped>
@keyframes neon {
  0%,
  100% {
    filter: hue-rotate(0);
  }
  50% {
    filter: hue-rotate(360deg);
  }
}

@keyframes rain {
  0% {
    background-position: 0 0;
  }
  100% {
    background-position: 3% 100%;
  }
}

@keyframes rainOpacity {
  0%,
  100% {
   opacity: 0.5;
  }
  50% {
    opacity: 1;
  }
}

.main {
  background-image: url('/images/city.webp');
  background-position: 50% 80%;
  background-repeat: no-repeat;
  animation: neon 3s linear infinite;
}

.rain {
  background-image: url('/images/rain.png');
  animation: rain 0.5s linear infinite, rainOpacity 10s linear infinite;
}
</style>