<script setup lang="ts">
import { reactive, isReactive, toRaw, markRaw } from "vue"

const state = { count: 1 }
const reactiveState = reactive(state)

/**
 * 修改以下代码使输出为true
*/
console.log(toRaw(reactiveState) === state)

/**
 * 修改以下代码使输出为false
*/

const info = { count: 1 }  // 这边添加markRaw  也就是下面的reactive是无效的 可以嵌套在其他的对象里 那个对象的这个值同样是不可以被proxy的
const reactiveInfo = reactive(info)  

console.log(isReactive(reactiveInfo))

</script>

<template>
  <div>
    <p>
      {{ reactiveState.count }}
    </p>
  </div>
</template>

