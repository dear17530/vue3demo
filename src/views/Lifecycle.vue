<template>
  <div ref="refDiv">{{ text }}</div>
  <button @click="change">改字</button>
</template>

<script setup>
import {
  ref,
  onBeforeMount,
  onMounted,
  onBeforeUpdate,
  onUpdated,
  onBeforeUnmount,
  onUnmounted
} from 'vue'

const refDiv = ref(null)
const text = ref('div')

console.log('setup(created)', refDiv.value)

const change = () => {
  console.log('click change')
  text.value = 'new div'
}

onBeforeMount(() => {
  console.log('onBeforeMount', refDiv.value)
})

onMounted(() => {
  console.log('onMounted', refDiv.value)
})

onBeforeUpdate(() => {
  console.log('onBeforeUpdate', refDiv.value.outerHTML)
})

onUpdated(() => {
  console.log('onUpdated', refDiv.value.outerHTML)
})

onBeforeUnmount(() => {
  console.log('onBeforeUnmount')
})

const count = ref()
count.value = setInterval(() => {
  console.log(1)
}, 1000)

onUnmounted(() => {
  console.log('onUnmounted')
  if (count.value) clearInterval(count.value)
})
</script>
