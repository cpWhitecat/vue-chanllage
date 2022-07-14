<script setup lang='ts'>

import { ref , computed } from "vue"

/**
 * 实现`useLocalStorage`函数
*/
function useLocalStorage(key: string, initialValue: any) {
  const value = ref(initialValue)
	const localValue = computed({
    get:initialValue=>{
      return localStorage.getItem(key)
			
    },
    set:initialValue=>{
			localStorage.setItem(key,value.value)
  	}
  })
  return localValue
}

const counter = useLocalStorage("counter", 0)

// 我们可以通过触发`counter`的`getter`来获取本地存储的值
console.log(counter.value)

// 同样地,我们也可以通过触发`counter`的`setter`来设置本地存储的值

counter.value = 1

</script>
