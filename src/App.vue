<template>
  <RouterView />
</template>

<script setup>
import { RouterView } from 'vue-router'
</script>

<style>
body {
  background: #000;
  color: #fff;
  padding: 30px;
}

.mr-1 {
  margin-right: 3px;
}

.red {
  background: red;
}

.blue {
  background: blue;
}

.white {
  background: #fff;
}

.box {
  width: 300px;
  height: 20px;
  margin-bottom: 5px;
}

input {
  margin-left: 10px;
}
</style>
