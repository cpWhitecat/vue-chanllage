<script setup lang='ts'>
import { ref , watch } from "vue"

const count = ref(0)

/**
 * 实现`until`函数
*/

function until(initial) {  //可以做个判断 initial是否ref  
  function toBe(value) {
    return new Promise((resolve,reject)=>{
        watch(count,()=>{
            if (initial.value == value) {
                resolve(clearInterval)
            }
        })
    })
  }

  return {
    toBe,
  }
}

async function increase() {
  count.value = 0
  setInterval(() => {
    count.value++
  }, 1000);

  await until(count).toBe(3)
  console.log(count.value === 3) // 确保输出为true
}

</script>
