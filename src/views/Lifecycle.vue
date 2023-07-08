<template>
  <div ref="refDiv">{{ text }}</div>
  <button @click="change">改字</button>

  <div>{{ person.name }}</div>
  <div>{{ person.num }}</div>
  <div>computed: {{ rename }}</div>

  <button @click="changeName">改名</button>
  <button @click="() => person.num++">++</button>
</template>

<script setup>
import { ref, reactive, watch, computed } from 'vue'

const refDiv = ref(null)
const text = ref('div')
const person = reactive({
  name: 'KT',
  num: 1
})

const change = () => {
  console.log('click change')
  text.value = 'new div'
}

const changeName = () => {
  console.log('click changeName')
  person.name = 'KT2'
}

const rename = computed(() => person.name + person.num)

watch(
  () => text.value,
  (nv, ov) => {
    console.log('watch text nv', nv)
    console.log('watch text ov', ov)
  }
)

watch(
  () => ({ ...person }),
  (nv, ov) => {
    console.log('watch person nv', nv)
    console.log('watch person ov', ov)
  }
)

watch(
  () => rename.value,
  (nv, ov) => {
    console.log('watch rename nv', nv)
    console.log('watch rename ov', ov)
  }
)
</script>
