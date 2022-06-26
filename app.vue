<script setup lang="ts">
let number = ref(0)
const list = ref([1, 2, 3, 4, 5, 6, 7, 8, 9, 10])

const pColor = ref("red")

function handleClick() {
  number.value++
  pColor.value = randomColor()
}

function randomColor(): string {
  const colors = ["red", "green", "yellow", "blue"]
  const index = Math.random() * 3 >> 0
  return colors[index]
}

function handleClear() {
  number.value = 0
}
</script>

<template>
  <div>
    <h1>Heading tag</h1>
    <h2>My first website</h2>
    <button @click="handleClick">Click me</button>
    <button @click="handleClear" v-if="number >= 10">Clear</button>
    <p>Number of clicks: {{ number }}</p>

    <div v-if="number < 10">
      Too small
    </div>
    <div v-else-if="number >= 10 && number < 20">
      Just enough
    </div>
    <div v-else>
      Too large
    </div>

    <div v-for="item in list" :key="item">
      <p :style="{color: pColor, fontSize: `${number}px`}">{{ item }}</p>
    </div>
  </div>
</template>

<style>
body {
  padding: 0;
  margin: 0;
}

h1 {
  width: 100%;
  text-align: center;
  background-color: green;
  color: white;
  margin: 0;
}

button {
  box-shadow: 0 0 8px 4px lightgrey;
}
</style>
