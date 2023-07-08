<template>
  <!-- 顯示文字 -->
  <h4>顯示文字</h4>
  <div>{{ name }}</div>
  <div v-text="name"></div>

  <br />

  <!-- 顯示HTML -->
  <h4>顯示HTML</h4>
  <div v-html="html"></div>

  <br />

  <!-- 條件顯示 -->
  <h4>v-if 條件顯示</h4>
  <div v-if="KT == 1">KT1</div>
  <div v-else-if="KT == 2">KT2</div>
  <div v-else>KT3</div>

  <h4>v-show條件顯示</h4>
  <div v-show="KT == 2">KT2</div>

  <br />

  <!-- for 迴圈[Arr] -->
  <h4>for 迴圈[Arr]</h4>
  <ul>
    <li v-for="item in array" :key="item">{{ item }}</li>
    <li v-for="(item, index) in array" :key="item">{{ index }}</li>
    <li style="color: red" v-for="(item, index) in array" :key="item">{{ index + 1 }}</li>
  </ul>

  <br />
  <!-- for 迴圈[Arr] -->
  <h4>for 迴圈[obj]</h4>
  <ul>
    <template v-for="item in obj" :key="item">
      <li>name: {{ item.name }}</li>
      <li>age: {{ item.age }}</li>
    </template>
  </ul>

  <br />

  <!-- 綁定屬性 -->
  <h4>綁定屬性</h4>
  <img class="mr-1" v-bind:src="image" />
  <img :src="image" />

  <br />

  <!-- 綁定 style，裡面要放 json，key 是樣式名，value 是樣式屬性 -->
  <h4>綁定 style</h4>
  <div class="box" style="border: 10px solid blue" />
  <div class="box" :style="{ border: redBorder }" />
  <div class="box" :style="myborder" />

  <br />

  <!-- 綁定 class -->
  <h4>綁定 class</h4>
  <div class="box" :class="{ blue: true }"></div>
  <div class="box" :class="whiteBg ? 'white' : 'red'"></div>
  <div class="box" :class="{ red: redBg }"></div>

  <br />

  <!-- 綁定 input -->
  <h4>綁定 input</h4>
  v-model<input type="text" v-model="inputText" />inputText: {{ inputText }}
  <br />
  修飾符 v-model.trim<input type="text" v-model.trim="inputTextTrim" />inputTextTrim:
  {{ inputTextTrim }}
  <br />
  修飾符 v-model.lazy<input type="text" v-model.lazy="inputTextLazy" />inputTextLazy:
  {{ inputTextLazy }}
  <br />
  修飾符 v-model.number<input type="text" v-model.number="inputTextNum" />inputTextNum:
  {{ inputTextNum }}
  <br />
  <br />

  <!-- 綁定 checkbox -->
  <h4>綁定 checkbox</h4>
  <label>
    <input type="checkbox" name="1" v-model="checkValue" :value="1" />
    1
  </label>
  <label>
    <input type="checkbox" name="2" v-model="checkValue" :value="2" />
    2
  </label>
  checkValue: {{ checkValue }}
  <br />
  <br />

  <!-- 綁定 radio -->
  <h4>綁定 radio</h4>
  <label>
    <input type="radio" v-model="radioValue" :value="1" />
    1
  </label>
  <label>
    <input type="radio" v-model="radioValue" :value="2" />
    2
  </label>
  radio: {{ radioValue }}

  <br />
  <br />

  <!-- 綁定 textarea -->
  <h4>綁定 textarea</h4>
  <textarea v-model="message" />
  <div>{{ message }}</div>
  <br />

  <!-- 綁定 select -->
  <h4>綁定 select</h4>
  <select v-model="selected">
    <option>A</option>
    <option>B</option>
    <option>C</option>
  </select>
  select: {{ selected }}

  <br />
  <br />

  <!-- 綁定 multiple select -->
  <h4>綁定 multiple select</h4>
  <select v-model="selecteMultiple" multiple>
    <option>A</option>
    <option>B</option>
    <option>C</option>
  </select>
  selecteMultiple: {{ selecteMultiple }}
  <br />
</template>

<script setup>
import { ref } from 'vue'

const name = ref('KT')
const html = ref('<span style="color: red">KT2</span>')
const KT = ref(1)
const array = ['KT', 'KT1', 'KT2']
const obj = [
  {
    name: 'KT1',
    age: 10
  },
  {
    name: 'KT2',
    age: 20
  },
  {
    name: 'KT3',
    age: 30
  }
]
const image = 'https://fakeimg.pl/250x100/'
const redBorder = '10px solid white'
const myborder = { border: '10px solid red' }
const disabled = ref(true)
const redBg = ref(true)
const whiteBg = ref(true)
const inputText = ref(1234)
const inputTextTrim = ref(1234)
const inputTextLazy = ref(1234)
const inputTextNum = ref(1234)
const checkValue = ref([])
const radioValue = ref()
const message = ref('')
const selected = ref('')
const selecteMultiple = ref([])
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
