<script setup lang='ts'>
import { reactive, ref , toRefs } from 'vue';


/**
 * 实现一个切换状态的可组合函数
 * 确保该功能正常工作
*/
function useToggle(flag:boolean) {  //这边的boolean不能加 这会导致return 的值必须包含boolean类型
    let AA = ref(flag)



    const toggle = ()=>{
        AA.value = ! AA.value
    }
    return [AA,toggle]
};

const [state, toggle] = useToggle(false)

</script>

<template>
  <p>State: {{ state ? 'ON' : 'OFF' }}</p>
  <p @click="toggle">
    Toggle state
  </p>
</template>
