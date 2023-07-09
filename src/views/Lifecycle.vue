<template>
  <input
    v-for="item in colorList"
    :key="item.name"
    type="radio"
    v-model="color"
    :value="item.color"
  />
  <ul>
    <li class="color">123</li>
  </ul>
</template>

<script setup>
import { ref, reactive } from 'vue'

const colorList = reactive([
  {
    name: 'red',
    color: 'red'
  },
  {
    name: 'blue',
    color: 'blue'
  }
])

const color = ref(colorList[0].color)
</script>

<style>
.color {
  color: v-bind('color');
}
</style>
