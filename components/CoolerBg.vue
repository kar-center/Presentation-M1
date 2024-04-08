<template>
  <div class="absolute top-0 left-0 h-full w-full">
    <div class="relative w-full h-full">
      <div v-for="(l,i) in positions" :key="i" class="absolute bubble"
           :style="{
              left: `${l.left}%`,
              top: `${l.top}%`,
              '--size': `${l.size}px`,
              opacity: Math.random()*0.8
           }"
      >

      </div>
    </div>
  </div>
</template>
<script setup lang="ts">
import {useIntervalFn} from "@vueuse/core"
import {ref} from "vue";

interface Location {
  top: number
  left: number
  size: number
}


const positions = ref<Location[]>([
  {left: 0, top: 0, size: 0},
  {left: 0, top: 0, size: 0},
  {left: 0, top: 0, size: 0},
])

setTimeout(()=>{
  positions.value = positions.value.map(it => {
    it.left = Math.random() * 100
    it.top = Math.random() * 100
    it.size = 100 * Math.random()
    return it
  })
}, 200)

useIntervalFn(() => {
  console.log('tick')
  positions.value = positions.value.map(it => {
    it.left = Math.random() * 100
    it.top = Math.random() * 100
    it.size = 100 * Math.random()
    return it
  })
}, 4000)


</script>
<style scoped>
.bubble {
  transition: all 4s ease-in-out;
  box-shadow: 0 0 1000px var(--size) limegreen;
  z-index: -200;
}

</style>
