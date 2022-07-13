// Child.vue

<script setup lang="ts">
import { onMounted, inject, onBeforeUnmount } from "vue"

const timer = inject('timer')
const count = inject('count')


onMounted(() => {
    //定时器重复，每次切换组件删除就行
  // The timer will work abnormally when the child component is toggled. Lets fix it.
  timer.value = window.setInterval(() => {
    count.value++
  }, 1000)
})

onBeforeUnmount(()=>{
    window.clearInterval(timer.value)
})
</script>

<template>
  <div>
    <p>
      Child Component: {{ count }}
    </p>
  </div>
</template>
