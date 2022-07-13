<script setup>
const text = ref();
function toUpper(text){
    text.value = text.value.charAt(0).toUpperCase + text.value.slice(1)
}
</script>

<template>
  <input ref=text type="text" v-model.capitalize="toUpper" />
</template>