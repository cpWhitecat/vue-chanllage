<script setup lang='ts'>
import {ref , toRefs} from 'vue'
interface UseCounterOptions {
  min?: number
  max?: number
}

/**
 * 实现计数器函数,确保功能正常工作
 * 1. 加 (+)
 * 2. 减 (-)
 * 3. 重置 
 * 4. 最小值 & 最大值 选项支持   //这个需求没读懂
*/
function useCounter(initialValue = 0, options: UseCounterOptions = {}) {
    const init = 0;
    const value = ref(initialValue);
    const inc = ()=>{
        value.value++
    };

    const dec = ()=>{
        value.value--
    };

    const reset = ()=>{
        value.value = init
    }

    return {
        count :toRefs(value),
        inc,
        dec,
        reset
        }

}

const { count, inc, dec, reset } = useCounter(0, { min: 0, max: 10 })

</script>
