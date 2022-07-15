<script setup lang='ts'>

import { ref , computed } from "vue"

/**
 * 实现`useLocalStorage`函数
*/
function useLocalStorage(key: string, initialValue: any) {
  const value = ref(initialValue)
	const localValue = computed({
    get:()=>{
      localStorage.getItem(key);
      return value.value  //原先这里是返回localStorage.getItem(key) 这会存在一个问题 万一get不到呢 所以下面才会报错
			
    },
    set:newVal=>{
      value.value = newVal //之前的错误找到了 ，set方法忘记给被proxy的值赋值了 ，传值也搞错了
			return localStorage.setItem(key,newVal)
      
  	}
  })
  return localValue
}

const counter = useLocalStorage("counter", 0)

// 我们可以通过触发`counter`的`getter`来获取本地存储的值
console.log(counter.value)

// 同样地,我们也可以通过触发`counter`的`setter`来设置本地存储的值

counter.value = 1
const update = ()=>{
  counter.value++
}

</script>

<template>
  <p>Counter: {{ counter }}</p>
  <button @click="update">
    Update
  </button>
</template>
