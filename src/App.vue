<script setup lang="ts">
import { ref } from "vue";
import getRandomEmoji from "./util/getRandomEmoji";

const items = ref(["😏", "😐", "😑", "😒", "😕", "❤", "🌹", "🦄"]);

const removeItem = (item: string) => {
  items.value = items.value.filter((i) => i !== item);
};

const addItem = () => {
  const newEmoji = getRandomEmoji();
  items.value = [...items.value, newEmoji];
};
</script>

<template>
  <h5>Click emojis to remove them.</h5>
  <ul v-auto-animate>
    <li v-for="item in items" :key="item" @click="removeItem(item)">
      {{ item }}
    </li>
  </ul>
  <div>
    <button @click="addItem">Add random emoji</button>
  </div>
  <div>
    <a href="https://auto-animate.formkit.com/#examples" target="_blank"
      >Examples</a
    >
  </div>
</template>

<style scoped>
ul {
  list-style: none;
  display: flex;
  flex-wrap: nowrap;
  user-select: none;
  max-height: 2em;
}
li {
  border: 1px solid #878787;
  border-radius: 5px;
  width: 2em;
  height: 2em;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-right: 0.5em;
  cursor: pointer;
}
</style>
