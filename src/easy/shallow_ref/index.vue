<script setup lang="ts">
import { shallowRef, triggerRef, watch } from "vue"

const state = shallowRef({ count: 1 })

// 回调没被触发
watch(state, () => {
  console.log("State.count Updated")
}, { deep: true })

// deep 是没有用的 shallow ref 只是对value层进行代理  

/**
 * 修改以下代码使watch回调被触发
 *
*/

// 直接修改覆盖掉原来的值 这会触发shallowRef 同时也会触发副作用
state.value = {
    count : 2
}


</script>

<template>
  <div>
    <p>
      {{ state.count }}
    </p>
  </div>
</template>
