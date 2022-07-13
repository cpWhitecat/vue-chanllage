<script setup lang="ts">

const click1 = () => {
  console.log('click1')
}

const click2 = () => {
  console.log('click2')
}

</script>

<template>
  <div @click="click1()">
   <div @click.stop="click2()">  // 事件执行机制导致 不停止冒泡会触发click1（）
     click me
   </div>
  </div>
</template>