<script setup lang="ts">
import { ref, onMounted } from 'vue'

const wrapper = ref<null | HTMLElement>(null)
const options = {
  threshold: 0.5,
}

onMounted(() => {
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting) {
        wrapper.value?.classList.add('animated')
        setTimeout(()=> {
            wrapper.value?.classList.add('hoverAdded')
        }, 2000)
      }else {
        wrapper.value?.classList.remove('animated')
        wrapper.value?.classList.remove('hoverAdded')
      }
    })
  }, options)
  if(wrapper.value) observer.observe(wrapper.value)
})
</script>

<template>
  <div class="relative h-screen">
    <div
      ref="wrapper"
      class="hoverAdded absolute left-1/2 top-1/2 -translate-x-1/2 -translate-y-1/2 text-8xl font-bold uppercase text-transparent cursor-pointer"
    >
      Belieeve
      <span class="believe first absolute top-0 left-0 text-black">Belieeve</span>
      <span class="believe second absolute top-0 left-0 text-black">Belieeve</span>
      <span
        class="text absolute top-1/2 left-0 ml-1.5 pl-5 text-2xl font-semibold text-center text-black bg-[#ff0]"
        >in yourself</span
      >
    </div>
  </div>
</template>


<style scoped>
@keyframes pushTopEffect {
  0%,
  100% {
    top: 0;
  }
  50% {
    top: -18px;
  }
}
@keyframes pushBottomEffect {
  0%,
  100% {
    top: 0;
  }
  50% {
    top: 18px;
  }
}
@keyframes showEffect {
  0%,
  100% {
    transform: translateY(-50%) scaleY(0);
  }
  50% {
    transform: translateY(-50%) scaleY(1);
  }
}

.believe {
  transition: 0.5s;
  overflow: hidden;
}
.first {
  clip-path: polygon(0 0, 100% 0, 100% 50%, 0 50%);
}
.second {
  clip-path: polygon(0 50%, 100% 50%, 100% 100%, 0 100%);
}
.text {
  width: calc(100% - 10px);
  letter-spacing: 0.7em;
  transition: 0.5s;
  transform: translateY(-50%) scaleY(0);
}
.hoverAdded:hover .first {
  transform: translateY(-18px);
}
.hoverAdded:hover .second {
  transform: translateY(18px);
}
.hoverAdded:hover .text {
  transform: translateY(-50%) scaleY(1);
}

.animated .first {
  animation: pushTopEffect 1s ease 0.5s 1;
}

.animated .second {
  animation: pushBottomEffect 1s ease 0.5s 1;
}
.animated .text {
  animation: showEffect 1s ease 0.5s 1;
}
</style>