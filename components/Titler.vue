<template>
  <div class="flex flex-col gap-[1.5rem]">
    <div class="flex flex-row justify-between items-center">
      <h2 style="font-size: 30px;">{{title}}</h2>
      <p v-if="pageNumber" class="w-[2rem] text-center h-[2rem] border rounded-[100%] ml-3" style="line-height: 33px">{{pageNumber}}</p>
    </div>
    <hr/>
  </div>
</template>
<script setup>
const props = defineProps(['title', 'pageNumber'])
</script>
<style scoped>

</style>